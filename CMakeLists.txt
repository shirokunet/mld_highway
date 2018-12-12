cmake_minimum_required(VERSION 2.8)
project(mld_highway)

# Create Main project
set(SOURCES
    src/main.cpp
    src/LaneDetection.cpp
    src/ParticleFilter.cpp
    src/util.cpp
)

set(HEADERS
    # main.h
    src/LaneDetection.h
    src/ParticleFilter.h
    src/util.h
)

add_executable(mld_highway
    ${SOURCES}
    ${HEADERS}
)


# For OpenCV
find_package(OpenCV REQUIRED)
if(OpenCV_FOUND)
    target_include_directories(mld_highway PUBLIC ${OpenCV_INCLUDE_DIRS})
    target_link_libraries(mld_highway ${OpenCV_LIBS})
endif()


# JSONCPP
find_package(PkgConfig REQUIRED)
pkg_check_modules(JSONCPP jsoncpp)
target_include_directories(mld_highway PUBLIC ${JSONCPP_INCLUDE_DIRS})
target_link_libraries(mld_highway ${JSONCPP_LIBRARIES})
