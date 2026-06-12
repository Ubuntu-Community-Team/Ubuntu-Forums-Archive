---
title: "wubi8.10 with windows7 now updated, can´t boot Ubuntu for new paths."
date: 2010-03-03
forum: General Help
---

### Post by sailorwolff on 2010-03-03
hi Gurus..

i got a new win 7 instalation after the beta ran out two days ago.
before that i had my beloved ubuntu 8.10 fully working and configured bootable.
i now installed win7 in a new partition and it cannot boot the WUBI instalation anymore. Ubuntu is on an own partition and still there and not touched.

my ex bootfile of the win7 bootloader:

There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Windows 7

Entry #1

Name:  Windows 7
BCD ID:  {default}
Drive: Deleted Partition
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Ubuntu
BCD ID:  {95e709a8-b562-11de-b6e4-ceed952ab549}
Drive:  K:\
Bootloader Path:  \ubuntu\winboot\wubildr.mbr


and my new one:

There is one entry in the Vista Bootloader.
Bootloader Timeout: 30 seconds.
Default OS: Windows 7

Entry #1

Name:  Windows 7
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

ubuntu is still in ¨K¨ as in the old bootloader.

how can i edit the vista bootloader that i can access my Ubuntu partiton again with the win7 bootloader? sorry for the more windows related question,**but maybe WUBI has a feature to repair the bootloader and grant new access?**
i use EASYBCD 1.7.2 for viewing the bootloder settings and it doesn´t let me edit the .txt file for the entries.

thank you guys in advance for your ideas.

Adam

---

### Post by oldfred on 2010-03-03
There is a howto Vista & Seven should be the same:

[[IMG]http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=1198406") [B]      Howto: Add a Wubi boot entry in Vista  
[http://ubuntuforums.org/showthread.php?t=1198406](http://ubuntuforums.org/showthread.php?t=1198406)
[/B]

---

### Post by sailorwolff on 2010-03-06
thanks a lot,
i now got the Ubuntu line in my windows 7 (vista) bootlader. the paths are set and it looks good. just when i try to boot into ubuntu, the loader starts to look for the wubildr in all the partitions and doesn´t find it.
i got win7 in the second partition on the second HD and ubuntu in the 4th partition on the second hard disk.
the drive letter of the ubuntu partition is K: and the path to the loader is 
K:/Ubuntu/winboot/wubildr
this path is set with easyBCD as recommended in the posting. there was no error and the path was accepted by bcd.
so what could be the problem? and is there a way of reconstruct the wubildr or do i have to install Wubi as well in win7?
if i install a new Wubi with the same paths, will it kill my old ubuntu installation?
how can i mount the ubuntu virtual disk in win7? no tool i tried so far works.
i should at least save some files before doing a new install. i still hope to get access to my ubuntu. it is (was) my first productive system.. (don´t ask why i did the win7 reinstall without saving all the Ubuntu datas..)
thanks a lot in advance for your help.
Adam

---

### Post by meierfra. on 2010-03-06
> K:/Ubuntu/winboot/wubildr

Try

K:/Ubuntu/winboot/wubildr[COLOR="Red"].mbr[/COLOR]

You might also try

K:/wubildr.mbr

and

C:/wubildr.mbr

---

