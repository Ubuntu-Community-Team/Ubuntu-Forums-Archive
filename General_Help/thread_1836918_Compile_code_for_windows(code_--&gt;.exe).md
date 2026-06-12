---
title: "Compile code for windows?(code --&gt;.exe)"
date: 2011-08-31
forum: General Help
---

### Post by al1x on 2011-08-31
[LEFT]Hello there,
I'am writing some simple programs in C++ and I want to share them with some friends who use windows.So I was wondering how can I compile to .exe executable instead of .out.Maybe I need to install wine...hmm, and then?[/LEFT]

---

### Post by pjd99 on 2011-08-31
Install mingw, its in the repositories. It will allow you to cross-compile for windows 32 or 64 bit architecture.

After a quick google search, found this:
[http://www.blogcompiler.com/2010/07/11/compile-for-windows-on-linux/](http://www.blogcompiler.com/2010/07/11/compile-for-windows-on-linux/)

Seems to be a decent starting point I think.

---

### Post by al1x on 2011-09-01
Thanks a lot , the blog seems to explain very good how to install mingw but I can't finally compile the program.When I run the     following command ```
/opt/mingw32/bin/i686-w64-mingw32-gcc /tmp/hello.c -o /tmp/hello-w32.exe
```terminal prints the following message```
bash: /opt/mingw32/W32_173611/bin/i686-w64-mingw32-gcc: cannot execute binary file
```
Also, when I run this command ```
/opt/mingw64/mingw64/bin/x86_64-w64-mingw32-gcc.exe main.cpp 

``` I get this message ```
run-detectors: unable to find an interpreter for
/opt/mingw64/mingw64/bin/x86_64-w64-mingw32-gcc.exe
``` :confused:

---

### Post by al1x on 2011-09-01
Maybe remove them and install them via the ubuntu software center?

---

### Post by decrepit on 2011-09-01
I'm far from an expert, but it looks like you're trying to execute a windows program, (.exe)?

---

### Post by al1x on 2011-09-01
> **decrepit said:**
> I'm far from an expert, but it looks like you're trying to execute a windows program, (.exe)?

Yep, I know that but this program is supposed to be for compiling for win32 and 64 while running linux!Also, if you read the instructions on the blog it says to execute this command...

---

### Post by cipherboy_loc on 2011-09-01
Another possible way is to use Wine. I don't have it installed at the moment, but it adds a wine-gcc command or something of the sort. With Wine you can test your programs to make sure they work.


Cipherboy.

---

### Post by donkyhotay on 2011-09-01
You might have better luck posting your question in the [packaging and compiling sub-forum](http://ubuntuforums.org/forumdisplay.php?f=44). Also do a google search for "how to cross compile with mingw" and see what you can find.

---

### Post by al1x on 2011-09-01
I'll check it and if it doesn't work I'll try it with wine.Thanks!

---

### Post by pjd99 on 2011-09-01
> **al1x said:**
> Thanks a lot , the blog seems to explain very good how to install mingw but I can't finally compile the program.When I run the     following command ```
/opt/mingw32/bin/i686-w64-mingw32-gcc /tmp/hello.c -o /tmp/hello-w32.exe
```terminal prints the following message```
bash: /opt/mingw32/W32_173611/bin/i686-w64-mingw32-gcc: cannot execute binary file
```
By the looks of it, this command tries to compile a 32-bit windows binary from a 32-bit version of gcc. Are you using a 64-bit OS? I'd try as others have suggested and install mingw from the repositories. You can check the installed paths of the mingw binaries/libraries by right-clicking the installed package in Synaptic and clicking properties.


> **al1x said:**
> Also, when I run this command  ```
/opt/mingw64/mingw64/bin/x86_64-w64-mingw32-gcc.exe main.cpp 

``` I get this message ```
run-detectors: unable to find an interpreter for
/opt/mingw64/mingw64/bin/x86_64-w64-mingw32-gcc.exe
``` :confused:
That won't work, you're trying to run a windows executable. You could possibly run it with wine, but that wouldn't be cross-compiling anyway.

---

### Post by al1x on 2011-09-05
> Are you using a 64-bit OS?
No, It's 32-bit.

I have installed MingW32 from the repositories but when I run the MingW32 version of gcc I get some errors and nothing happens...I consulted the CodeBlocks forum ([http://forums.codeblocks.org/index.php?topic=3343.0]("http://forums.codeblocks.org/index.php?topic=3343.0")) but I can't find and download insight.exe in order to proceed this Howto...(the download link which is posted it doesn't respond).
This site [http://sourceware.org/insight/downloads.php]("http://sourceware.org/insight/downloads.php") provides a version of insight which I can't extract using wine.

---

### Post by Matpen on 2011-11-04
[Here]("http://blog.kermat.net/blog5.php/cross-compilation-with-qt") you can find a full tutorial on how to cross-compile on Ubuntu for Windows, using Qt. However, if you do not use qt, only part of that tutorial is needed. Essentially, it boils down to this:
```

apt-get install build-essential mingw32
i586-mingw32msvc-gcc main.c -o main.exe

```
Of course, use the exact name of your program file instead of "main.c".

---

### Post by Todd Carnes on 2011-11-23
> **Matpen said:**
> [Here]("http://blog.kermat.net/blog5.php/cross-compilation-with-qt") you can find a full tutorial on how to cross-compile on Ubuntu for Windows, using Qt. However, if you do not use qt, only part of that tutorial is needed. Essentially, it boils down to this:
```

apt-get install build-essential mingw32
i586-mingw32msvc-gcc main.c -o main.exe

```Of course, use the exact name of your program file instead of "main.c".

If the OP follows the directions that you have "boiled it down to", they WON'T be successful. Simply installing the mingw32 compiler, then trying to invoke it as you directed results in a slew of unresolved dependencies for even a simple program.

---

### Post by mikejonesey on 2011-11-23
> **al1x said:**
> No, It's 32-bit.

I have installed MingW32 from the repositories but when I run the MingW32 version of gcc I get some errors and nothing happens...I consulted the CodeBlocks forum ([http://forums.codeblocks.org/index.php?topic=3343.0](http://forums.codeblocks.org/index.php?topic=3343.0)) but I can't find and download insight.exe in order to proceed this Howto...(the download link which is posted it doesn't respond).
This site [http://sourceware.org/insight/downloads.php](http://sourceware.org/insight/downloads.php) provides a version of insight which I can't extract using wine.

Hiya I cross compile often enough, you don't need insight to get up and running, this is optional (I have never used it)... ps C::B (codeblocks) is my fav ide for c++

 i've subscribed to this thread...

---

