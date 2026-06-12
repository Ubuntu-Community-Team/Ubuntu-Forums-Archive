---
title: "Workarounds for the problems in  mingw-w64 packages?"
date: 2011-03-12
forum: General Help
---

### Post by outofsync on 2011-03-12
_Short version of the question:_
Can I download, from somewhere, precompiled packages of the 4.5.x versions of mingw-w64, gcc-mingw32, mingw32-binutils, and mingw32-runtime, for Ubuntu Maverick? Does it matter if I install 4.5.x mingw32 while I use gcc 4.4.x on my machine? (I assume mingw32 is independent from the system gcc, but I ask because I'm not 100% sure)


_Long version of the question:_ (you don't need to read it if you know some solution to the "short version" above) ;)
I'm on Maverick 10.10. I've installed mingw-w64, gcc-mingw32, mingw32-binutils, and mingw32-runtime, in order to crosscompile from Linux to Windows.

I suceeded crosscompiling to 32bit windows (i586-mingw32msvc host)

However, when trying to crosscompile to 64bit windows (amd64-mingw32msvc host), I found there's no amd64-mingw32msvc-g++ compiler (there's a reported bug about this: [https://bugs.launchpad.net/ubuntu/+source/gcc-mingw32/+bug/568028](https://bugs.launchpad.net/ubuntu/+source/gcc-mingw32/+bug/568028)

To make things worse, I found this webpage stating that 4.4.x mingw64 produces unusable x86_64 executables: [http://openfoamwiki.net/index.php/Tip_Cross_Compiling_OpenFOAM_1.7_in_Linux_For_Windows_with_MinGW#Tweaking_environment_options](http://openfoamwiki.net/index.php/Tip_Cross_Compiling_OpenFOAM_1.7_in_Linux_For_Windows_with_MinGW#Tweaking_environment_options)

Such page says that 4.5.x mingw64 works fine. The problem is that Ubuntu provides 4.4.x ones, and also lacks g++

So, I need a working mingw64 g++, and also from the 4.5.x version, because I need to produce correct 64bit windows executables.

Any help greatly appreciated (I hope I won't need to compile the crosscompilers myself, as I'll be really lost at knowing what to do to manually replace the mingw-w64, gcc-mingw32, mingw32-binutils, and mingw32-runtime packages.

TIA

---

### Post by outofsync on 2011-03-12
Btw, I forgot to say I'm on 64bit Maverick

---

### Post by outofsync on 2011-03-12
The solution I found is to download the precompiled versions available at the mingw-w64 sourceforge page. You don't need to install them system-wide, you can put them in any directory you wish, provided that you put its "bin" subdir in the PATH.

That's the best workaround I found. Certainly the Ubuntu packages are not functional at this time, for the reasons explained above.

---

### Post by Matpen on 2011-03-12
Same problem here. I am trying to build a cross compilation environment with qt, and thus installed the same packages as outofsync.

This works for win32, but fails for win64:

```

matteo@ubuntubox:/tmp/qt-win-64$ amd64-mingw32msvc-g++ main.cpp -o test.exe
amd64-mingw32msvc-g++: command not found
matteo@ubuntubox:/tmp/qt-win-64$ amd64-mingw32msvc-gcc main.cpp -o test.exe
amd64-mingw32msvc-gcc: main.cpp: C++ compiler not installed on this system

```

I am on Maverick 64bit, too.

After reading the [bug description]("https://bugs.launchpad.net/ubuntu/+source/gcc-mingw32/+bug/568028") I tried to use pali's ppa:

```

sudo apt-get remove mingw-w64
sudo add-apt-repository ppa:pali
sudo add-apt-repository ppa:pali/ppa
sudo add-apt-repository ppa:mingw-packages/ppa
sudo apt-get update
sudo apt-get install mingw-w64

```

but this was no help.

---

### Post by Matpen on 2011-03-12
[This page]("http://mstenberg.com/blog/2010/07/11/compile-for-windows-on-linux/") explains the workaround in detail.

---

### Post by Matpen on 2011-03-15
I contacted Pali, who was kind enough to provide a [better solution]("https://bugs.launchpad.net/ubuntu/+source/gcc-mingw32/+bug/568028"):

Download the newer packages from the mingw-packages ppa repository (these are not only for karmic, they work on maverick, too):
```

wget http://ppa.launchpad.net/mingw-packages/ppa/ubuntu/pool/main/w/w64-toolchain/i686-w64-mingw32-toolchain_1.0b+201011211643-0w2273g93970b22426p16~karmic1_amd64.deb
wget http://ppa.launchpad.net/mingw-packages/ppa/ubuntu/pool/main/w/w64-toolchain/x86-64-w64-mingw32-toolchain_1.0b+201011211643-0w2273g93970b22426p16~karmic1_amd64.deb

```
Make sure you choose the correct architecture for your system (amd64/i386)!

Install some dependencies:
```

sudo apt-get install libcloog-ppl0 libgmpxx4ldbl libmpfr1ldbl libppl-c2 libppl7

```

Finally install the downloaded packages:
```

dpkg -i i686-w64-mingw32-toolchain_1.0b+201011211643-0w2273g93970b22426p16~karmic1_amd64.deb
dpkg -i x86-64-w64-mingw32-toolchain_1.0b+201011211643-0w2273g93970b22426p16~karmic1_amd64.deb

```

Enjoy your new compilers like this:
```

i686-w64-mingw32-gcc main.cpp -o main.exe
i686-w64-mingw32-g++ main.cpp -o main.exe
x86_64-w64-mingw32-gcc main.cpp -o main.exe
x86_64-w64-mingw32-g++ main.cpp -o main.exe

```

---

### Post by mihir123 on 2012-04-13
Hello

[http://mstenberg.com/blog/2010/07/11/compile-for-windows-on-linux/](http://mstenberg.com/blog/2010/07/11/compile-for-windows-on-linux/)

this one is also not working.

---

