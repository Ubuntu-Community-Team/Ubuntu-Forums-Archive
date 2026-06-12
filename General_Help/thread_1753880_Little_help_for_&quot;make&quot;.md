---
title: "Little help for &quot;make&quot;"
date: 2011-05-09
forum: General Help
---

### Post by teddy92 on 2011-05-09
hello everyone!
I'm trying to install a plugin for compiz that enables anaglyph 3d output:
Guide: [http://trycatch.iblogger.org/tips-n-tricks/3d-ubuntu](http://trycatch.iblogger.org/tips-n-tricks/3d-ubuntu)
I downloaded the files and then the guide says to do "make" and then "make install" (nothing about ./configure) but it fails saying "No makefile found" (obviously, because it isn't there).
Then i looked in the folder and i found a Cmakelists.txt file so i tryed cmake but nothing....

here is the folder tree:
.
&#9500;&#9472;&#9472; anaglyph
&#9474;   &#9500;&#9472;&#9472; anaglyph.xml.in
&#9474;   &#9500;&#9472;&#9472; CMakeCache.txt
&#9474;   &#9500;&#9472;&#9472; CMakeFiles
&#9474;   &#9474;   &#9500;&#9472;&#9472; CMakeCCompiler.cmake
&#9474;   &#9474;   &#9500;&#9472;&#9472; cmake.check_cache
&#9474;   &#9474;   &#9500;&#9472;&#9472; CMakeCXXCompiler.cmake
&#9474;   &#9474;   &#9500;&#9472;&#9472; CMakeDetermineCompilerABI_C.bin
&#9474;   &#9474;   &#9500;&#9472;&#9472; CMakeDetermineCompilerABI_CXX.bin
&#9474;   &#9474;   &#9500;&#9472;&#9472; CMakeOutput.log
&#9474;   &#9474;   &#9500;&#9472;&#9472; CMakeSystem.cmake
&#9474;   &#9474;   &#9500;&#9472;&#9472; CMakeTmp
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; CMakeFiles
&#9474;   &#9474;   &#9474;       &#9492;&#9472;&#9472; cmTryCompileExec.dir
&#9474;   &#9474;   &#9500;&#9472;&#9472; CompilerIdC
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; a.out
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; CMakeCCompilerId.c
&#9474;   &#9474;   &#9492;&#9472;&#9472; CompilerIdCXX
&#9474;   &#9474;       &#9500;&#9472;&#9472; a.out
&#9474;   &#9474;       &#9492;&#9472;&#9472; CMakeCXXCompilerId.cpp
&#9474;   &#9500;&#9472;&#9472; CMakeLists.txt
&#9474;   &#9492;&#9472;&#9472; src
&#9474;       &#9500;&#9472;&#9472; anaglyph.cpp
&#9474;       &#9492;&#9472;&#9472; anaglyph.h
&#9492;&#9472;&#9472; tree.txt

could someone help me please?
i'm on ubuntu 11.04
thanks in advance

---

### Post by mc4man on 2011-05-09
You are showing a lot of cmake generated files so not sure what you've done (or where you got them

Typically here with sources like this would do like - 
get the source, (git clone ...) and cd to folder (in this case anaglyph
Then - 
```
mkdir build && cd build
cmake ..
make
```

I wouldn't count on this working w/ the compiz used on 11.04 (0.9.4

Ex. of building from git clone

> doug@doug-XPS-M1330:~/anaglyph$ mkdir build && cd build
doug@doug-XPS-M1330:~/anaglyph/build$ cmake ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'compiz'
--   found compiz, version 0.9.4.0
-- Performing Test HAVE_SCANDIR_POSIX
-- Performing Test HAVE_SCANDIR_POSIX - Success
-- Boost version: 1.42.0
-- Found the following Boost libraries:
--   serialization
-- checking for module 'compiz-composite'
--   found compiz-composite, version 0.9.4.0
-- checking for module 'compiz-opengl'
--   found compiz-opengl, version 0.9.4.0
-- Configuring done
-- Generating done
-- Build files have been written to: /home/doug/anaglyph/build
doug@doug-XPS-M1330:~/anaglyph/build$ make
[ 16%] Generating generated/anaglyph.xml
[ 33%] Generating generated/compiz-anaglyph.schemas
[ 50%] Generating generated/anaglyph_options.h
[ 66%] Generating generated/anaglyph_options.cpp
Scanning dependencies of target anaglyph
[ 83%] Building CXX object CMakeFiles/anaglyph.dir/src/anaglyph.cpp.o
[100%] Building CXX object CMakeFiles/anaglyph.dir/generated/anaglyph_options.cpp.o
Linking CXX shared library libanaglyph.so
[100%] Built target anaglyph

Then do a sudo make install

---

### Post by teddy92 on 2011-05-09
thanks a lot for the reply, but it seems it doesn't work with this version of compiz :(

---

