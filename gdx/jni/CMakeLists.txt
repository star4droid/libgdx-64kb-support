cmake_minimum_required(VERSION 3.10)
project(gdx)

# ملفات المصدر الخاصة بالمكتبة
file(GLOB GDX_SRC
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
)

# إنشاء مكتبة مشتركة
add_library(gdx SHARED ${GDX_SRC})

# استخدام C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# محاذاة الصفحة 16KB
set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -Wl,--page-size=16384")

# ربط مكتبة log على Android
find_library(log-lib log)
target_link_libraries(gdx ${log-lib})
