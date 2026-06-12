---
title: "Wubi fails to uninstall"
date: 2010-03-19
forum: General Help
---

### Post by schoft on 2010-03-19
Going into my 5th day on trying to get linux to work on my system. I first tried a backtrack DVD but it failed to install after a kernel panic. I tried using ubuntu 9 and 8 but they both freezed at the livecd menu in bios and gave an i/o error. 

So I tried using WUBI but after choosing "UBUNTU" in the windows boot manager after the bios, it fails to load. So i try to uninstall Wubi, and i get this:

[img]http://img339.imageshack.us/img339/2998/wubilul.jpg[/img]

this is my logfile ( warning: .txt 500kb ) [http://www.clicka.nl/SDK/wubi-9.10ubuntu1-rev160.log](http://www.clicka.nl/SDK/wubi-9.10ubuntu1-rev160.log)

I'm guessing there is something very wrong with my pc, due to the i/o errors with both the ubuntu cd's and BT4.

Specs:
Windows 7 x64
4gb normal ram
q6600

Any help would be appreciated.

---

### Post by schoft on 2010-03-19
I first installed Wubi on an external HDD. It showed up in the windows boot manager but it wouldnt work. I uninstalled, and installed it on one of my regular disks. It wouldnt even show up the bootmanager anymore. And now i cant uninstall. I deleted everything under D:\Ubuntu. I feel like such a noob.

---

### Post by schoft on 2010-03-19
easyBCD says:

```
There is one entry in the Windows Vista bootloader.

Default: Windows 7
Timeout: 10 seconds.
EasyBCD Boot Device: C:\

Entry #1
Name: Windows 7
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe
```

Can someone give me a push in the right direction

---

### Post by schoft on 2010-03-19
Solved by deleting everything that mentioned "Wubi" in the registry.

---

