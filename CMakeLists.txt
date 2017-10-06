cmake_minimum_required(VERSION 3.8)
project(imgTransition)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES
        lib/SOIL/image_DXT.c
        lib/SOIL/image_helper.c
        lib/SOIL/SOIL.c
        lib/SOIL/stb_image_aug.c
        main.c)

IF(APPLE)
    INCLUDE_DIRECTORIES ( /System/Library/Frameworks )
    FIND_LIBRARY(COCOA_LIBRARY Cocoa)
    FIND_LIBRARY(GLUT_LIBRARY GLUT )
    FIND_LIBRARY(OpenGL_LIBRARY OpenGL )
    MARK_AS_ADVANCED (COCOA_LIBRARY
            GLUT_LIBRARY
            OpenGL_LIBRARY)
    SET(EXTRA_LIBS ${COCOA_LIBRARY} ${GLUT_LIBRARY} ${OpenGL_LIBRARY})
ELSE()
    SET(EXTRA_LIBS m GL GLU glut)
ENDIF()

add_executable(imgTransition ${SOURCE_FILES})
target_link_libraries(imgTransition ${EXTRA_LIBS})