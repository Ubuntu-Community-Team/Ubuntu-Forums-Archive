---
title: "*Please* help w/ dual boot (from noob)"
date: 2010-10-08
forum: General Help
---

### Post by spankler on 2010-10-08
I have a new (to me) system w/ ubuntu 10.04 installed and I would like  to do a dual boot w/ Windows (I have XP and 7 (32 & 64 bit) disks--both .iso's). I  have no exp. w/ linux generally and limited w/ Windows. I have  successfully installed the XP on my iMac using Parallels so I know the  disk is OK. On Ubuntu, when I open the XP .iso, it shows no mountable  items. With the 7, Ubuntu is treating as a archive, which it is not. The  message reads: 

"Archive: /media/UDF Volume/setup.exe
[/media/UDF Volume/setup.exe]
     End-of-central-directory signature not found. Either this file is not a  zipfile, or it constitutes one disk of a multi-part archive. In the  latter case the central directory and zipfile comment will be found on  the last disk(s) of this archive.
note: /media/UDF Volume/setup.exe may be a plain executable, not an archive.
zipinfo: cannot find zipfile directory in one of /media/UDF Volume/setup.exe.ZIP, period."

One  question is, why is it being treated as a zipfile when it is not?  Secondly, I read it is better to install Windows first, so I tried  reformatting the disk and got this message:

"Error creating filesystem
An  error occurred while performing an operation on :78 GB Filesystem"  (Partition 1 of ATA WDC WD800BB-75JHC0): The device is busy

-Details
/dev/sda1 is mounted"

How do I proceed? Please help!:confused:

---

### Post by andrewthomas on 2010-10-08
If you want to install windows, then you have to **change the boot order in BIOS** in order to select the CD/DVD drive first.

---

