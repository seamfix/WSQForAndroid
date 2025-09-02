# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

# Set code endianness to little endian; most (all?) Android platforms are little endian
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -D__NBISLE__")

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.

add_library( # Sets the name of the library.
             wsq

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
        nbis/imgtools/src/lib/wsq/cropcoeff.c
        nbis/imgtools/src/lib/wsq/decoder.c
        nbis/imgtools/src/lib/wsq/encoder.c
        nbis/imgtools/src/lib/wsq/globals.c
        nbis/imgtools/src/lib/wsq/huff.c
        nbis/imgtools/src/lib/wsq/ppi.c
        nbis/imgtools/src/lib/wsq/sd14util.c
        nbis/imgtools/src/lib/wsq/tableio.c
        nbis/imgtools/src/lib/wsq/tree.c
        nbis/imgtools/src/lib/wsq/util.c
        nbis/imgtools/src/lib/jpegl/decoder.c
        nbis/imgtools/src/lib/jpegl/encoder.c
        nbis/imgtools/src/lib/jpegl/huff.c
        nbis/imgtools/src/lib/jpegl/huftable.c
        nbis/imgtools/src/lib/jpegl/imgdat.c
        nbis/imgtools/src/lib/jpegl/ppi.c
        nbis/imgtools/src/lib/jpegl/sd4util.c
        nbis/imgtools/src/lib/jpegl/tableio.c
        nbis/imgtools/src/lib/jpegl/util.c
        nbis/imgtools/src/lib/image/img_io.c
        nbis/imgtools/src/lib/image/readihdr.c
        nbis/imgtools/src/lib/image/imgutil.c
        nbis/imgtools/src/lib/image/rl.c
        nbis/imgtools/src/lib/image/grp4deco.c
        nbis/imgtools/src/lib/image/imageops.c
        nbis/imgtools/src/lib/ihead/getcomp.c
        nbis/imgtools/src/lib/ihead/getnset.c
        nbis/imgtools/src/lib/ihead/nullihdr.c
        nbis/imgtools/src/lib/ihead/parsihdr.c
        nbis/imgtools/src/lib/ihead/prntihdr.c
        nbis/imgtools/src/lib/ihead/readihdr.c
        nbis/imgtools/src/lib/ihead/valdcomp.c
        nbis/imgtools/src/lib/ihead/writihdr.c
        nbis/commonnbis/src/lib/ioutil/dataio.c
        nbis/commonnbis/src/lib/ioutil/fileexst.c
        nbis/commonnbis/src/lib/ioutil/filehead.c
        nbis/commonnbis/src/lib/ioutil/fileroot.c
        nbis/commonnbis/src/lib/ioutil/filesize.c
        nbis/commonnbis/src/lib/ioutil/filetail.c
        nbis/commonnbis/src/lib/ioutil/findfile.c
        nbis/commonnbis/src/lib/ioutil/newext.c
        nbis/commonnbis/src/lib/ioutil/readutil.c
        nbis/commonnbis/src/lib/util/bres.c
        nbis/commonnbis/src/lib/util/bubble.c
        nbis/commonnbis/src/lib/util/computil.c
        nbis/commonnbis/src/lib/util/fatalerr.c
        nbis/commonnbis/src/lib/util/invbyte.c
        nbis/commonnbis/src/lib/util/invbytes.c
        nbis/commonnbis/src/lib/util/memalloc.c
        nbis/commonnbis/src/lib/util/ssxstats.c
        nbis/commonnbis/src/lib/util/syserr.c
        nbis/commonnbis/src/lib/util/ticks.c
        nbis/commonnbis/src/lib/util/time.c
        nbis/commonnbis/src/lib/fet/allocfet.c
        nbis/commonnbis/src/lib/fet/delfet.c
        nbis/commonnbis/src/lib/fet/extrfet.c
        nbis/commonnbis/src/lib/fet/freefet.c
        nbis/commonnbis/src/lib/fet/lkupfet.c
        nbis/commonnbis/src/lib/fet/nistcom.c
        nbis/commonnbis/src/lib/fet/printfet.c
        nbis/commonnbis/src/lib/fet/readfet.c
        nbis/commonnbis/src/lib/fet/strfet.c
        nbis/commonnbis/src/lib/fet/updatfet.c
        nbis/commonnbis/src/lib/fet/writefet.c
        wsq.cpp
             )

target_include_directories(wsq PRIVATE nbis/imgtools/include nbis/commonnbis/include nbis/commonnbis/include/mlp)

# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
                       wsq

                       # Links the target library to the log library
                       # included in the NDK.
                       ${log-lib} )