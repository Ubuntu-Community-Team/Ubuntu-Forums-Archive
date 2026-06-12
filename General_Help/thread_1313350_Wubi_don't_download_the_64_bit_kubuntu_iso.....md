---
title: "Wubi don't download the 64 bit kubuntu iso...."
date: 2009-11-03
forum: General Help
---

### Post by actionman86 on 2009-11-03
hi guys, i have a problem that is driving me crazy... i want to install kubuntu 64bit by wubi but he download me the 32 bit version of kubuntu instead of the 64 bit one... I tryed everything i could, i downloaded the iso, mounted the image and masterized it, but no way, wubi wants the 32 but wersion :(

What can i do???

---

### Post by pinko on 2009-11-13
Run wubi.exe

While running wubi locate the running pyrun.exe location (its an executable used by wubi) C:\Users\[user]\AppData\Local\Temp\pyl****.tmp goto the data folder and edit isolist.ini 
find [Kubuntu-amd64] heading make sure all files relating to amd64 are not uncommented including metalinks. This was the case with mine the metalink url was for i386 version and the amd64 version was uncommented.

---

### Post by Keiran230 on 2010-04-25
This is the exact same problem I had, but I found a solution:

[http://ubuntuforums.org/showthread.php?p=9140031](http://ubuntuforums.org/showthread.php?p=9140031)

**TL/DR**: Using this executable fixed it: [http://people.canonical.com/~evand/wubi/karmic/wubi-r168.exe](http://people.canonical.com/~evand/wubi/karmic/wubi-r168.exe)

---

