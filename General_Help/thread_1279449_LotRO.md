---
title: "LotRO"
date: 2009-09-30
forum: General Help
---

### Post by incanuso on 2009-09-30
I've been folowing this guide: 

[http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X](http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X)

and have done everything successfully so far except install the actual game. Every time I try, Wine says "opening lotrostandard.exe" then goes away and does nothing. When i try through the terminal, it gives me:

```
Log file is being written to C:\windows\temp\lotrostandard.exe.log
Exception in thread "LibgcjInternalFinalizerThread" java.lang.NullPointerException
   at 0x0069e20e (Unknown Source)
   at 0x0069e702 (Unknown Source)
   at 0x0069e7b3 (Unknown Source)
   at 0x00681a6d (Unknown Source)
   at 0x00691a2d (Unknown Source)
   at 0x006c742d (Unknown Source)
   at 0x00676af2 (Unknown Source)
   at 0x006c64d7 (Unknown Source)
   at 0x7b843dd3 (Unknown Source)
   at 0x7bc6e909 (Unknown Source)
   at 0x7bc6c1e5 (Unknown Source)
   at 0x7bc6c1b7 (Unknown Source)
   at 0x7bc6c759 (Unknown Source)
   at 0x7bc6d0c9 (Unknown Source)
   at 0x7bc6e160 (Unknown Source)
   at 0xdeadbaba (Unknown Source)
   at 0x006d1377 (Unknown Source)
   at 0x0072c297 (Unknown Source)
   at 0x006ca317 (Unknown Source)
   at 0x006a3440 (Unknown Source)
   at 0x006d1e1c (Unknown Source)
   at 0x00732cc5 (Unknown Source)
   at 0x7bc6c180 (Unknown Source)
   at 0x7bc6c39c (Unknown Source)
   at 0x7bc745e7 (Unknown Source)
   at 0xb7e224fb (Unknown Source)

```I don't know what to do.

---

### Post by coldReactive on 2009-09-30
Is wine version 1.0.1 or 1.1.30? If it's the former, get the latest from here: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and try again. After completely removing wine, and the installed applications you installed (you have to uninstall the applications in wine before you remove wine.)

---

### Post by incanuso on 2009-09-30
It's the second. I installed ubuntu earlier today.

---

### Post by coldReactive on 2009-09-30
Then it's best to file a bug report or bring it up on the winehq forums.

Also, don't be discouraged if it works for someone else, but not you, it happens a lot that way.

---

### Post by tnt533 on 2009-09-30
I've read that it is better to install the game on a windows system first and then copy over the files afterword. Just a thought.

---

### Post by coldReactive on 2009-09-30
> **tnt533 said:**
> I've read that it is better to install the game on a windows system first and then copy over the files afterword. Just a thought.

That's where most people get the "worksforme" let down when they report bugs. It's never a good idea to copy over a windows installation to wine and hope that it works (IE: Flash CS3.)

---

