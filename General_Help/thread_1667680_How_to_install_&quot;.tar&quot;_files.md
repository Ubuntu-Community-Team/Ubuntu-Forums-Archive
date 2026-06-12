---
title: "How to install &quot;.tar&quot; files?"
date: 2011-01-15
forum: General Help
---

### Post by Eneco on 2011-01-15
Hi,

I'm trying to install MemScanner but I can't install any .tar files. I have been trying to install .tar files weeks I have been trying too install different .tar files but I can't manage to install them. I know this has been posted many times before but every time I try to follow a guide it doesn't work. Could someone tell me exactly what to do please?

The file I am trying to install: [http://code.google.com/p/memscanner/]("http://code.google.com/p/memscanner/")

---

### Post by davidmohammed on 2011-01-15
ok - step by step

you downloaded the file - where? Assuming your download folders...


in a terminal type

cd Downloads

then unpack the tar file

tar -xvf memscanner-v1.3.tar 

this should unpack the tar file into a folder called memscanner

cd memscanner

type

cmake .

etc etc

---

### Post by WorMzy on 2011-01-15
tar files are just archives. You can no more install a tar on linux, than you can a zip on Windows. Assuming what you have downloaded is the source code, you need to compile it, and then install the compiled application. Check the readme it comes with, or the website you downloaded it from, for detailed instructions (hopefully).

---

### Post by Eneco on 2011-01-15
I got an error: 

```
travis@travis-R530-R730-P590:~$ cd Downloads
travis@travis-R530-R730-P590:~/Downloads$ tar -xvf memscanner-v1.3.tar 
memscanner/
memscanner/memscanner/
memscanner/memscanner/scan.h
memscanner/memscanner/mainwindow.h
memscanner/memscanner/themes.ui
memscanner/memscanner/pList/
memscanner/memscanner/pList/pList.cpp
memscanner/memscanner/pList/CMakeLists.txt
memscanner/memscanner/pList/pList.h
memscanner/memscanner/ranges.h
memscanner/memscanner/mainwindow.cpp
memscanner/memscanner/CMakeLists.txt
memscanner/memscanner/themes.cpp
memscanner/memscanner/main.cpp
memscanner/memscanner/resources.qrc
memscanner/memscanner/icons/
memscanner/memscanner/icons/stop.png
memscanner/memscanner/icons/board.png
memscanner/memscanner/icons/book.png
memscanner/memscanner/icons/edit.png
memscanner/memscanner/icons/note.png
memscanner/memscanner/icons/refresh.png
memscanner/memscanner/icons/delete.png
memscanner/memscanner/icons/arrow.png
memscanner/memscanner/icons/doc.png
memscanner/memscanner/icons/logout.png
memscanner/memscanner/icons/settings.png
memscanner/memscanner/icons/search.png
memscanner/memscanner/icons/undo.png
memscanner/memscanner/icons/exec.png
memscanner/memscanner/icons/new.png
memscanner/memscanner/icons/redo.png
memscanner/memscanner/mainwindow.ui
memscanner/memscanner/ranges.cpp
memscanner/memscanner/themes.h
memscanner/memscanner/scan.cpp
memscanner/CMakeLists.txt
memscanner/cmake_uninstall.cmake.in
travis@travis-R530-R730-P590:~/Downloads$ cd memscanner
travis@travis-R530-R730-P590:~/Downloads/memscanner$ cmake .
-- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at /usr/share/cmake-2.8/Modules/FindQt4.cmake:1151 (MESSAGE):
  Qt qmake not found!
Call Stack (most recent call first):
  CMakeLists.txt:3 (find_package)


-- Configuring incomplete, errors occurred!
travis@travis-R530-R730-P590:~/Downloads/memscanner$ 
```


What do I do? :confused:

---

### Post by davidmohammed on 2011-01-15
ok - you need to install some QT stuff to compile against

suggest type the following:


sudo apt-get install qt4-qmake
sudo apt-get install libqt4-dev


then try again with

cmake . etc etc

---

### Post by Eneco on 2011-01-15
I installed those two packages and it still doesn't work. :(


```
travis@travis-R530-R730-P590:~/Downloads/memscanner$ cmake .
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring incomplete, errors occurred!
travis@travis-R530-R730-P590:~/Downloads/memscanner$ 

```

---

### Post by davidmohammed on 2011-01-15
try 

sudo apt-get install cmake build-essential

---

### Post by ZebaSz on 2011-01-15
Although I don't know how to solve your specific problem, I do suggest that you replace
```
sudo make install
```
with
```
sudo checkinstall
```
make install could cause conflicts in the future, since it circumvents the package manager.
To do this, you must run:
```
sudo apt-get install checkinstall
```

---

### Post by Eneco on 2011-01-15
> **davidmohammed said:**
> try 

sudo apt-get install cmake build-essential

Thanks for your help. :)

I managed to install it.

---

