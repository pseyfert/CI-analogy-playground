#cmake_minimum_required(VERSION 3.0)
include(CheckCXXCompilerFlag)

macro(AddCXXFlagIfSupported flag test) 
  CHECK_CXX_COMPILER_FLAG(${flag} ${test}) 
  if( ${${test}} ) 
    message("adding ${flag}") 
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${flag}") 
  endif() 
endmacro() 

AddCXXFlagIfSupported(-fdiagnostics-color=$ENV{DIAG_COLOR} COMPILER_SUPPORTS_fdiagnostics-color) 

AddCXXFlagIfSupported(-Wall COMPILER_SUPPORTS_Wall) 
AddCXXFlagIfSupported(-Wextra COMPILER_SUPPORTS_Wextra) 

add_executable(hello hello.cpp)
