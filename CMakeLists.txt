cmake_minimum_required(VERSION 3.20.2)

project(test-wxwidgets VERSION 1.0.0)

find_package(wxWidgets REQUIRED COMPONENTS core base)

include("${wxWidgets_USE_FILE}")

add_executable(test-wxwidgets
    src/cApp.cpp
    src/cMain.cpp
    include/cApp.h
    include/cMain.h
)

target_include_directories(test-wxwidgets PRIVATE include ${wxWidgets_INCLUDE_DIRS})

target_link_libraries(test-wxwidgets PRIVATE ${wxWidgets_LIBRARIES})

target_compile_definitions(test-wxwidgets PRIVATE ${wxWidgets_DEFINITIONS} ${wxWidgets_DEFINITIONS_DEBUG})

target_link_options(test-wxwidgets PRIVATE "/SUBSYSTEM:WINDOWS")

target_compile_options(test-wxwidgets PRIVATE ${wxWidgets_CXX_FLAGS})