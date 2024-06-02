cmake_minimum_required(VERSION 3.22)
project(yolov8)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_BUILD_TYPE Release) # None, Debug, Release, RelWithDebInfo, MinSizeRel
#SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -Wno-unused-parameter -O0 -g -Wall")
#SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS}  -Wno-unused-parameter -O0 -g -Wall")
SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O3 -g")
SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -g")

include_directories(include)

add_subdirectory(utils)

find_package(spdlog REQUIRED)

find_package(bytetrack REQUIRED)

find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

add_executable(imagefile_demo imagefile_demo.cpp)
target_link_libraries(imagefile_demo ${OpenCV_LIBS} ${bytetrack_LIBS} spdlog::spdlog yolov8_lib)
