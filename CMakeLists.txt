cmake_minimum_required(VERSION 3.22.0..3.25.0)

project(itk-examples
  LANGUAGES CXX C
)


if(NOT CMAKE_INSTALL_PREFIX)
  set(CMAKE_INSTALL_PREFIX
  "${CMAKE_BINARY_DIR}/install"
  CACHE STRING "Final install location." FORCE)
endif()

#==============================================================================
# Set the global output paths
#==============================================================================
set(
  CMAKE_ARCHIVE_OUTPUT_DIRECTORY
  ${CMAKE_BINARY_DIR}/lib
  CACHE STRING "" FORCE
)

set(
  CMAKE_LIBRARY_OUTPUT_DIRECTORY
  ${CMAKE_BINARY_DIR}/lib
  CACHE STRING "" FORCE
)

set(
  CMAKE_RUNTIME_OUTPUT_DIRECTORY
  ${CMAKE_BINARY_DIR}/bin
  CACHE STRING "" FORCE
)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

#==============================================================================
# Set the third party library paths
#==============================================================================
set(
  ITK_DIR
  ${CMAKE_SOURCE_DIR}/../ITK-build/dist/lib/cmake/ITK-5.4
  #${CMAKE_SOURCE_DIR}/externals/ITK/lib/cmake/ITK-5.4
  CACHE
  STRING ""
  FORCE
)

set(
  VTK_DIR
  #${CMAKE_SOURCE_DIR}/externals/VTK/lib/cmake/vtk-9.2
  ${CMAKE_SOURCE_DIR}/../VTK-build/dist/lib/cmake/vtk-9.2
  CACHE
  STRING ""
  FORCE
)

find_package(ITK REQUIRED)
include(${ITK_USE_FILE})

set(ITK_TEST_DRIVER itkTestDriver)
# set(ITK_BUILD_DEFAULT_MODULES ON CACHE BOOL "" FORCE)
add_subdirectory(Iterators)
add_subdirectory(DataRepresentation)
add_subdirectory(Filtering)
add_subdirectory(IO)
add_subdirectory(Numerics)
add_subdirectory(Segmentation)
add_subdirectory(SpatialObjects)
add_subdirectory(Statistics)
add_subdirectory(RegistrationITKv4)
