cmake_minimum_required(VERSION 3.8)
project(ros2_reflexxes)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include_directories(include)

add_library(reflexxes SHARED
src/TypeIIRML/ReflexxesAPI.cpp
src/TypeIIRML/TypeIIRMLCalculatePositionalExtrems.cpp
src/TypeIIRML/TypeIIRMLDecisions.cpp
src/TypeIIRML/TypeIIRMLDecisionTree1A.cpp
src/TypeIIRML/TypeIIRMLDecisionTree1B.cpp
src/TypeIIRML/TypeIIRMLDecisionTree1C.cpp
src/TypeIIRML/TypeIIRMLDecisionTree2.cpp
src/TypeIIRML/TypeIIRMLFallBackStrategy.cpp
src/TypeIIRML/TypeIIRMLIsPhaseSynchronizationPossible.cpp
src/TypeIIRML/TypeIIRMLPolynomial.cpp
src/TypeIIRML/TypeIIRMLPosition.cpp
src/TypeIIRML/TypeIIRMLQuicksort.cpp
src/TypeIIRML/TypeIIRMLSetupModifiedSelectionVector.cpp
src/TypeIIRML/TypeIIRMLStep1.cpp
src/TypeIIRML/TypeIIRMLStep1IntermediateProfiles.cpp
src/TypeIIRML/TypeIIRMLStep1Profiles.cpp
src/TypeIIRML/TypeIIRMLStep2.cpp
src/TypeIIRML/TypeIIRMLStep2IntermediateProfiles.cpp
src/TypeIIRML/TypeIIRMLStep2PhaseSynchronization.cpp
src/TypeIIRML/TypeIIRMLStep2Profiles.cpp
src/TypeIIRML/TypeIIRMLStep2WithoutSynchronization.cpp
src/TypeIIRML/TypeIIRMLStep3.cpp
src/TypeIIRML/TypeIIRMLVelocityCalculatePositionalExtrems.cpp
src/TypeIIRML/TypeIIRMLVelocity.cpp
src/TypeIIRML/TypeIIRMLVelocityFallBackStrategy.cpp
src/TypeIIRML/TypeIIRMLVelocityIsPhaseSynchronizationPossible.cpp
src/TypeIIRML/TypeIIRMLVelocityMethods.cpp
src/TypeIIRML/TypeIIRMLVelocitySetupPhaseSyncSelectionVector.cpp
)

install(TARGETS reflexxes LIBRARY DESTINATION lib)
install(DIRECTORY include/ DESTINATION include)

ament_export_include_directories(include)
ament_export_libraries(reflexxes)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # uncomment the line when a copyright and license is not present in all source files
  #set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # uncomment the line when this package is not in a git repo
  #set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
