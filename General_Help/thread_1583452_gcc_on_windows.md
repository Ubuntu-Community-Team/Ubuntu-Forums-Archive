---
title: "gcc on windows"
date: 2010-09-27
forum: General Help
---

### Post by utkarshjadhav on 2010-09-27
folks, plz temme how to install GCC on windows.
from where to download the setup file?
I googled it -but couldnt find a good solution.
F1!!

---

### Post by qamelian on 2010-09-27
You can find GCC and other GNU tools at [http://www.gnu.org](http://www.gnu.org).

---

### Post by Iowan on 2010-09-27
There is at least one package for Windows that uses GCC... check [http://www.bloodshed.net/devcpp.html]("http://www.bloodshed.net/devcpp.html")

---

### Post by Tibuda on 2010-09-27
[http://www.mingw.org/](http://www.mingw.org/)

---

### Post by srs5694 on 2010-09-28
There are at least two different implementations of GCC for Windows. One is [MinGW,](http://www.mingw.org) which Tibuda has mentioned. This version has the advantage of being able to produce standalone Windows applications that can run on any Windows system. There's also a cross-compiler, so you can compile Windows binaries on a Linux system. (Some of the Windows binaries of my [GPT fdisk program](http://sourceforge.net/projects/gptfdisk/files/) are compiled this way, although I generally prefer to use Microsoft's Visual C++ for this because it produces smaller binaries.)

Another GCC implementation for Windows is part of the [Cygwin](http://www.cygwin.com) package. I'm less familiar with this one, but my impression is that you need to have at least parts of Cygwin installed to run the programs compiled using Cygwin's GCC. OTOH, if you want a Unix-like environment in Windows, Cygwin is very useful; it provides an X server and lots of Unix commands and utilities.

There are probably other GCC implementations for Windows, but I don't know much about them. Googling "Windows GCC" produces a lot of hits, and some sound like GCC versions for Windows other than MinGW or Cygwin.

Also, if you don't need GCC specifically, you should be aware that Microsoft makes its [Visual C++ Express](http://www.microsoft.com/express/windows/) available for free. IIRC, you've got to register to get it, but there's no charge to obtain or use it. It includes a nice GUI IDE. The main practical reason to favor MinGW or Cygwin's GCC would be if you want to compile software written for Unix or Linux, which includes Unix/Linux-style file I/O or other platform-specific features. Such programs might not compile properly under Visual C++. Of course, if you'd rather use GPLed software, that rules out Visual C++.

---

