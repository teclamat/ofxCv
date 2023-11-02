find_package(OpenCV REQUIRED)
find_package(Freetype REQUIRED)

set(OFX_CV_SOURCES
  libs/CLD/src/ETF.cpp
  libs/CLD/src/fdog.cpp
  libs/ofxCv/src/Calibration.cpp
  libs/ofxCv/src/ContourFinder.cpp
  libs/ofxCv/src/Distance.cpp
  libs/ofxCv/src/Flow.cpp
  libs/ofxCv/src/Helpers.cpp
  libs/ofxCv/src/Kalman.cpp
  libs/ofxCv/src/ObjectFinder.cpp
  libs/ofxCv/src/RunningBackground.cpp
  libs/ofxCv/src/Tracker.cpp
  libs/ofxCv/src/Utilities.cpp
  libs/ofxCv/src/Wrappers.cpp
)
add_library(ofxCv STATIC ${OFX_CV_SOURCES})
add_library(ofx::Cv ALIAS ofxCv)
target_include_directories(ofxCv PUBLIC
  ${CMAKE_CURRENT_SOURCE_DIR}/src
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/CLD/include/CLD
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/ofxCv/include
  ${OpenCV_INCLUDE_DIRS}
)
target_link_libraries(ofxCv PUBLIC openFrameworks ${OpenCV_LIBS} Freetype::Freetype)
