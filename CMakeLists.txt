cmake_minimum_required(VERSION 3.14)

project(create-gp4)
include(ExternalProject)

if (WIN32)
    set(TOOL_NAME create-gp4.exe)
else()
    set(TOOL_NAME create-gp4)
endif()

ExternalProject_Add(create-gp4
    LOG_CONFIGURE YES
    LOG_BUILD YES
    LOG_INSTALL YES
    LOG_OUTPUT_ON_FAILURE YES
    SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/cmd/create-gp4
    CONFIGURE_COMMAND ""
    BUILD_COMMAND go build -o ${TOOL_NAME}
    BUILD_IN_SOURCE 1
    INSTALL_COMMAND ""
)
set(CREATE_GP4_BINARY ${CMAKE_CURRENT_SOURCE_DIR}/cmd/create-gp4/${TOOL_NAME})
