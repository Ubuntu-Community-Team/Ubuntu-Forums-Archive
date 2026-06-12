---
title: "What I need to add in Windows boot.ini ?"
date: 2009-09-01
forum: General Help
---

### Post by csh on 2009-09-01
I reinstalled Windows XP. Before doing that, I backup the wubildr and wubildr.mbr files in C:\ drive to another partition. The original Ubuntu installation directory is in D:\ drive, so it is not affected by re-installation of Windows.

But, I forgot to make a backup copy of boot.ini. Both wubildr and wubildr.mbr has been restored to C:\ drive.

So, can anybody tell me what statements I need to add in boot.ini file?

Any reply will be appreciated. Thank you!!!

---

### Post by Neill_R on 2009-09-01
Here is my BOOT.INI


you have to know the partitioning of your drive(s) and the installation directory name
Here I have two version of windows XP and one installation of Windows ME
hope this helps


                                       [boot loader]
    [LEFT]timeout=30[/LEFT]
    [LEFT]default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS[/LEFT]
    [LEFT][operating systems][/LEFT]
    [LEFT]multi(0)disk(0)rdisk(0)partition(6)\WINXP="Original WinXp" [/LEFT]
    [LEFT]multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="New WinXp"  [/LEFT]
    [LEFT]C:\="Microsoft Windows" [/LEFT]

---

