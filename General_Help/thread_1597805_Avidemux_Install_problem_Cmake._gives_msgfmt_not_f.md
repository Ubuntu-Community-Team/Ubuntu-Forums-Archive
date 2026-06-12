---
title: "Avidemux Install problem Cmake. gives msgfmt not found"
date: 2010-10-15
forum: General Help
---

### Post by cybermeid on 2010-10-15
I am trying to compile Avidemux 2.4.4 from the folder where it is installed.
When I type cmake. for compiling it is showing this error

> 
CMake Error at cmake/Po.cmake:11 (MESSAGE):
  msgfmt not found - po files can't be processed
Call Stack (most recent call first):
  cmake/Po.cmake:21 (FIND_MSGFMT)
  po/CMakeLists.txt:3 (COMPILE_PO_FILES)


After google searching through various forums I found an answer here
```
http://avidemux.org/admForum/viewtopic.php?id=4948
```

You have **msgfmt** somewhere in your system? (it should come with **gettext** package)
Yes right. gettext package was not installed. Thanks for quick response.  I tried to add this to Ubuntu specific compilation info on wiki but  page is locked. It is [http://www.avidemux.org/admWiki/index.p … 2FXubuntu.]("http://www.avidemux.org/admWiki/index.php?title=Compiling_Avidemux#Ubuntu.2FKubuntu.2FXubuntu.")


I guess they solved the problem.But I didnt understand what he meant by that as I already have gettext installed.Can someone help me with this?Thanks

---

### Post by cybermeid on 2010-10-19
Can somebody please help me with Avidemux installation.I am forced to put windows just for running Avidemux.Help please.

---

### Post by cybermeid on 2010-10-24
in this forum do anybody bother to help us out or is it just a gimmick?
ubuntu sucks I guess

---

