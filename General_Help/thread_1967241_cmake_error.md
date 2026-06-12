---
title: "cmake error?"
date: 2012-04-27
forum: General Help
---

### Post by raen on 2012-04-27
Despite having used Linux for the past three years, I'm still far from proficient at the command line.

I downloaded the program kxstitch ( [http://sourceforge.net/apps/mediawiki/kxstitch/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/kxstitch/index.php?title=Main_Page) ) and I'm trying to compile it. I already discovered that I had to install cmake, so I did that (sudo apt-get install cmake) but now I'm getting this:

```
raen@compy:~/Downloads/kxstitch-0.9.0-KDE4$ ./build.sh
-- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/raen/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:5 (find_package)


-- Configuring incomplete, errors occurred!

```What am I missing or doing wrong? (My /home is on a separate partition if that makes a difference.)

Thanks,
raen

---

### Post by raen on 2012-04-28
Well, I decided to be bold and trust in my Google-fu. Turned out I was going about it all kinds of wrong.

Credit to this guy here: [http://titaniumbunker.com/?p=1208](http://titaniumbunker.com/?p=1208)

Feeling simultaneously smarter and foolish,
raen

---

