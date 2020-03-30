cmake_minimum_required (VERSION 3.1)

project (Boilerplate)

add_executable(main
 ${PROJECT_SOURCE_DIR}/main.cpp
)

set_property(TARGET main PROPERTY CXX_STANDARD 11)
target_compile_options(main PRIVATE -Wall)

add_subdirectory(${PROJECT_SOURCE_DIR}/glfw EXCLUDE_FROM_ALL)
target_link_libraries(main PRIVATE glfw)

add_definitions(-DGLEW_STATIC)
add_subdirectory(${PROJECT_SOURCE_DIR}/glew EXCLUDE_FROM_ALL)
target_link_libraries(main PRIVATE libglew_static)

add_subdirectory(${PROJECT_SOURCE_DIR}/glm EXCLUDE_FROM_ALL)
target_link_libraries(main PRIVATE glm)

target_include_directories(main PRIVATE
    ${PROJECT_SOURCE_DIR}/imgui
)
set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT main)

