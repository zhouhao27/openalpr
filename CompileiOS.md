# Compile for iOS

## Leptonica
## Tesseact
## OpenCV

1. Download the source code

> git clone https://github.com/openalpr/openalpr.git

> cd openalpr

2. Copy dependecies to framework folder

Regarding with the compiling of the dependent libraris like opencv2.framework, leptonica.framework and tesseract.framework is another story.

3. Create the build folder in src

> cd src

> mkdir build

> cd build

4. Add iOS CMake toolchain from **Polly**

> git clone https://github.com/ruslo/polly.git

5. Generate the Xcode project for iOS

> export XCODE_XCCONFIG_FILE=$PWD/polly/scripts/NoCodeSign.xcconfig

> cmake .. -DCMAKE_TOOLCHAIN_FILE=./polly/ios-nocodesign-10-3.cmake  -DTesseract_FRAMEWORK_PATH=../frameworks/tesseract.framework -DOpenCV_FRAMEWORK_PATH=../frameworks/opencv2.framework -DLeptonica_FRAMEWORK_PATH=../frameworks/leptonica.framework -DOpenCV_VERSION=3.4.1 -DOpenCV_VERSION_MAJOR=3  -DWITH_DAEMON=OFF -DWITH_STATEDETECTION=ON -GXcode

**NOTICE:**

Got a compile error for "Can't find opencv2/*.hpp". 
I copy all files under opencv2.framework/Headers to opencv2.framework/Headers/opencv2. 


## References 

[Build universal library](https://www.raywenderlich.com/41377/creating-a-static-library-in-ios-tutorial)
