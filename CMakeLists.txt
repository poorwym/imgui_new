cmake_minimum_required(VERSION 3.10)
project(imgui)

set(CMAKE_CXX_STANDARD 14)

file(GLOB IMGUI_SOURCES
    *.cpp
    *.h
    backends/imgui_impl_glfw.cpp
    backends/imgui_impl_glfw.h
    backends/imgui_impl_vulkan.cpp
    backends/imgui_impl_vulkan.h
)
find_package(Vulkan REQUIRED)

add_compile_definitions(IMGUI_IMPL_VULKAN_NO_PROTOTYPES)

add_library(imgui STATIC ${IMGUI_SOURCES})

target_include_directories(imgui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

target_link_libraries(imgui PUBLIC Vulkan::Vulkan)