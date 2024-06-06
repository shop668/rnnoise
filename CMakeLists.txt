cmake_minimum_required(VERSION 3.16)
project(rnnoise) 

cmake_policy(SET CMP0054 NEW)
set(CMAKE_CXX_STANDARD 17) 
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

include_directories("${PROJECT_SOURCE_DIR}/include")
include_directories("${PROJECT_SOURCE_DIR}/src")

set(RN_NOISE_SRC "src/denoise.c" "src/rnn.c" "src/pitch.c" "src/kiss_fft.c" "src/celt_lpc.c" "src/nnet.c" "src/nnet_default.c" "src/parse_lpcnet_weights.c" "src/rnnoise_data.c" "src/rnnoise_tables.c")

add_library(rnnoise SHARED ${RN_NOISE_SRC})
add_library(rnnoise_static STATIC ${RN_NOISE_SRC})
set_target_properties(rnnoise_static PROPERTIES OUTPUT_NAME "rnnoise")
