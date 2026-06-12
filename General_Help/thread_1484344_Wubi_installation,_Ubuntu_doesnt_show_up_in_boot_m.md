---
title: "Wubi installation, Ubuntu doesnt show up in boot menu"
date: 2010-05-15
forum: General Help
---

### Post by Atro on 2010-05-15
Hey guys

Installed Ubuntu 10.04 wubi today, then realized it was the 64 bit version. Unintsalled it and force installed the 32 bit version.

Got through the installation process, PC restarted and I got 2 Options.

Windows Vista
Ubuntu

When choosing ubuntu, it shows only one option which is Windows. When choosing that it goes back to the previous boot menu.

Here is the esyBCD output, 

There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Ubuntu
BCD ID:  {8221118a-458b-11de-8d7f-001966b1e836}
Drive:  E:\
Bootloader Path:  \ubuntu\winboot\wubildr.mbr

Will appreciate any help

---

