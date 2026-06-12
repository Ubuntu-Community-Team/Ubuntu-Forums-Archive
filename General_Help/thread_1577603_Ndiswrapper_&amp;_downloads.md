---
title: "Ndiswrapper &amp; downloads"
date: 2010-09-19
forum: General Help
---

### Post by tony044 on 2010-09-19
[B]I have NDISWRAPPER installed on my laptop, but when I try to install the download file which is a Windows Xp dos executable file of 8mbs I have tried every thing but without success I can see my Iomega 250 Zip drive when I go into system>administration>disk utilities and acess properties but cannot make it run, any ideas on how to get my zip drive working would be much appreciated.
Dell inspiron 6400
OS: Ubuntu 10.04LTS
Ram:2gb
HDD: 250gb
Tony044[/B]:guitar:

---

### Post by weblordpepe on 2010-09-19
Hi dude. If you are concerned with getting files out of that EXE then try the following:

If the EXE is a Windows program, download and install WINE. WINE will let you run it and extract whatever crap is inside. If the EXE is purely an MSDOS exe file then try using DOSBOX. Failing that, try running it on another computer thats got windows on it.

The linux kernel (the kernel is the core of linux) does have support for lots of things but they are disabled. Specifically old hardware. I heard this is the case with zip drives. Im no expert on this but there is a few programs that will let you actually adjust the parameters (turn on & off) support for all kinds of wacky strange stuff. You then then re-compile the kernel again and make a new kernel which runs on next boot.

---

