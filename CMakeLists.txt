cmake_minimum_required(VERSION 3.14)
project(MCL)

add_subdirectory(eigen-git-mirror)
find_package (Eigen3 3.3 REQUIRED NO_MODULE)

set(PEGTL_BUILD_EXAMPLES OFF CACHE BOOL "Nope" FORCE)
set(PEGTL_BUILD_TESTS OFF CACHE BOOL "Nope" FORCE)
add_subdirectory(PEGTL)
set(CMAKE_CXX_STANDARD 17)

add_executable(${PROJECT_NAME} main.cpp)

target_link_libraries (${PROJECT_NAME} 
LINK_PUBLIC Eigen3::Eigen 
LINK_PUBLIC taocpp::pegtl)

set(CMAKE_EXE_LINKER_FLAGS ${CMAKE_EXE_LINKER_FLAGS} "-static")