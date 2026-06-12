---
title: "Weird c compiler behaviour"
date: 2009-08-30
forum: General Help
---

### Post by rbaleksandar on 2009-08-30
Hi, guys.

  I'm very unhappy now,,,It started with the upgrade to Jaunty. I started getting the bloody error when compiling no matter what kind of a project...

```

-- The CXX compiler identification is unknown
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- broken
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
  The C++ compiler "/usr/bin/c++" is not able to compile a simple test
  program.

```

  I looked everywhere I could think of...Couldn't fix it. And since there were other buddy things that stopped working (like the Network Manager), I decided to reinstall my Ubuntu afresh - no upgrades from previous version, nothing.
  This didn't fix anything...Again - I wasn't able to compile a single simple C/C++ program with **cmake**. The same error haunted me even in my dreams... :-& Then today a miracle happened...I was reading [this]("https://wiki.ubuntu.com/PackagingGuide/Basic?action=show&redirect=HowToBuildDebianPackagesFromScratch") in order to avoid compiling it by hand (although executing **cmake**, than **make** and finally **make install** shouldn't be that difficult to do :)) and create a DEB-package from the source files (which worked on my previous Ubuntu - compiling and everything!). From the Synaptic Manager I downloaded/reinstalled all these:
**gnupg, lintian, fakeroot, pbuilder, debhelper and dh-make** in order to make sure everything's fresh and without me spoiling it. :D And here's where the miracle happened!!! Don't know why but I decided to try compiling the source files of the project I wanted to install previously and didn't succeed. Typed ```
cmake .
``` with trembeling fingers and sweat on my forehead. Pressed ENTER to execute the command...Boom! The console started telling me that everything's found and fine. Started compiling all the files. After that it got even better. I was able to execute ```
make
```! I stared at the display and the flying lines of comfirmation that this and that was compiled successfully etc. Then again - happiness isn't something that last long. For me it didn't last even a short period of time...Executing ```
make install
``` gave me thist:
```

[ 99%] Built target hedgewars
[100%] Built target hwengine
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/bin/hedgewars
CMake Error at QTfrontend/cmake_install.cmake:36 (FILE):
file INSTALL cannot copy file
"/home/rbaleksandar/Desktop/hedgewars-src-0.9.11/bin/hedgewars" to
"/usr/local/bin/hedgewars".
Call Stack (most recent call first):
cmake_install.cmake:38 (INCLUDE)

make: *** [install] Error 1
```
  I looked for this error on the internet...No success. Than I thought - hey, maybe recompiling the source will fix this...Accidents by compiling stuff happen. So I deleted the compiled files including the make-files.

  With by "great" luck after executing ```
cmake .
``` again I got the same errors of a broken C compiler as described above... :confused: :(
How can this be? First it's not working...Then it works...Then again it's not working?

  I can compile it with the LiveCD but that is far from an optimal solution since I have to reboot everytime I download source files that I want to compile and install...

  Can someone please help me? If possible - not too technical terminology.
Thanks in advance and best regards,
rbaleksandar

---

### Post by nhanquy on 2009-08-30
can not copy file?

looks like you need **sudo make install **?

---

### Post by rbaleksandar on 2009-08-30
> **nhanquy said:**
> can not copy file?

looks like you need **sudo make install **?

Ah, I forgot to install as a root. :( But i can't do this anymore since I can't compile the source again. 

Thanks for your fast reply.

---

### Post by Liolikas on 2009-08-30
Better try to use Debian package. Or double check if it exists (or not) in Ubuntu Synaptic. If not submit bug (feature request) for it.

Compile from source should be last resort solution only in almost any modern Linux distribution.

---

### Post by rbaleksandar on 2009-08-30
> **Liolikas said:**
> Better try to use Debian package. Or double check if it exists (or not) in Ubuntu Synaptic. If not submit bug (feature request) for it.

Compile from source should be last resort solution only in almost any modern Linux distribution.

  It has a deb-package, but it's an old version (about 3 versions older than the current). Besides - I want to fix this. Don't like it when somethings not working in the system as it's supposed to be.

---

### Post by Liolikas on 2009-08-30
Do like explained here:
[http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source](http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source)
If you succeed well share results with game site where you downloaded source.

---

### Post by rbaleksandar on 2009-08-30
> **Liolikas said:**
> Do like explained here:
[http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source](http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source)
If you succeed well share results with game site where you downloaded source.

  Actually that was the other thing with the DEB-package and building it - wanted to share it, so that someone with my problems can use it. Thanks. This looks much easier than the Packaging Guide in the Ubuntu Wiki. Will give it a try.

  Yet the compiler-problem and the solution remain an opened topic.


Thanks. :)

---

### Post by Liolikas on 2009-08-30
Hmm I looked once again and I think you forgot:
sudo make install

---

### Post by rbaleksandar on 2009-08-30
Dunno. Maybe I forgot. Will try after I can compile once again. :) Non the less - for compiling I don't need to be root. Installing - ok, there I need. But for now since I can't compile the source, I obviously can't install the program. :D

---

### Post by Liolikas on 2009-08-30
But for installing you need to be root!

---

### Post by rbaleksandar on 2009-08-30
> **Liolikas said:**
> But for installing you need to be root!
  I know, that's what I said. :) You're missing the point here - the **make install**-thing isn't bothering me that much as the fact I wasn't able to compile, than I was able to and than again I'm not able to. You have to admit that the behaviour of my compiler is weird. :D

---

### Post by Liolikas on 2009-08-30
No I will never admit that :P
From 1 post it looks like compiler works fine.

---

### Post by rbaleksandar on 2009-08-30
> **Liolikas said:**
> No I will never admit that :P
From 1 post it looks like compiler works fine.

:D Whut? Ok, here's a short version of what I wrote:


PREVIOUSLY:
  Trying to compile a source (**cmake . **) gave me the following output:
```

-- The CXX compiler identification is unknown
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- **broken**
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
  **The C++ compiler "/usr/bin/c++" is not able to compile a simple test program.**

```

THE MOMENT WHEN THE MIRACLE HAPPENED:
  Compiling worked for the first time. So did **make** work. Cmake and make don't need root to work. The first one is for compiling, the second one - for making the make-files that are used for the installation.
  Here's the thing with **sudo make install** that I most probably forgot to do (the sudo-part I mean). That's why I got the errors that INSTALL can't be copied.

LATER:
  Trying to compile a source (**cmake . **) gave me the following output:
```

-- The CXX compiler identification is unknown
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- **broken**
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
**The C++ compiler "/usr/bin/c++" is not able to compile a simple test program.**

```

  This isn't normal.

---

### Post by Liolikas on 2009-08-30
It may mean you simply lack libs. Read README file included in source. It should explain what you need before compiling (or what you need to compile first). This is all hard part and why *.debs are fun.

---

### Post by rbaleksandar on 2009-08-30
It needs:
[b]cmake
qt4-qmake
libqt4-dev
libsdl1.2-dev
libsdl-net1.2-dev
libsdl-mixer1.2-dev
libsdl-image1.2-dev
libsdl-ttf2.0-dev
fpc
ghc [/b](optional)

  This isn't from these source files in particular. It's with all that use the CXX compiler to be compiled. I've always noticed that the terminal tells you if you want to install something and something goes wrong. It tells you what's missing for the thing to be compiled. I don't have this problem with the Perl or Python compiler for example. It's only this one. Before installing/compiling I always check what's needed for thing to go as they are supposed to.

---

### Post by Liolikas on 2009-08-30
>It tells you what's missing for the thing to be compiled.
Not always.

Perl of Python is not compiler they just interpret scripts.

So just make sure you have all that black list in your system and correct versions and try again.
I ques you lack qt4-qmake

---

### Post by rbaleksandar on 2009-09-01
Nope, it's not Qt. And besides - it tells me that the CXX compiler (which I reinstalled a couple of times hoping that it'll run next time I use it) is broken.

---

