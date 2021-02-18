cmake_minimum_required (VERSION 3.8)

add_library (chopper_interface INTERFACE)
target_link_libraries (chopper_interface INTERFACE seqan3::seqan3)
target_include_directories (chopper_interface INTERFACE ../include)
target_include_directories (chopper_interface INTERFACE ../lib/lemon/include)
target_compile_definitions (chopper_interface INTERFACE ${SEQAN_DEFINITIONS})
target_compile_options (chopper_interface INTERFACE ${SEQAN_CXX_FLAGS_LIST})
target_link_libraries (chopper_interface INTERFACE "${SEQAN_LIBRARIES}")
target_include_directories (chopper_interface INTERFACE "${SEQAN_INCLUDE_DIRS}")

add_executable (chopper chopper.cpp)
target_link_libraries (chopper "chopper_interface")

add_executable (count_kmers_per_bin count_kmers_per_bin.cpp)
target_link_libraries (count_kmers_per_bin "chopper_interface")

add_executable (count_HIBF_kmers_based_on_binning count_HIBF_kmers_based_on_binning.cpp)
target_link_libraries (count_HIBF_kmers_based_on_binning "chopper_interface")

