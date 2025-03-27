cmake_minimum_required(VERSION 3.10)
project(gst_recording_project)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(PkgConfig REQUIRED)
pkg_check_modules(GST REQUIRED gstreamer-1.0 gstreamer-video-1.0 gstreamer-app-1.0)

include_directories(${GST_INCLUDE_DIRS} include)

add_executable(recording_app src/main.cpp src/command_handler.cpp)
target_link_libraries(recording_app ${GST_LIBRARIES})

add_subdirectory(plugins/recording_plugin)
add_subdirectory(plugins/deskew_plugin)
