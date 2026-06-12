---
title: "ext3 driver for windows 7?"
date: 2009-10-28
forum: General Help
---

### Post by pythonscript on 2009-10-28
I know this isn't exactly the place to ask this, but I figure ubuntu being one of the largest proponents of the ext system, at least someone should know. Does anyone know of a good driver that supports windows 7 x86/x64 to read ext3 file systems? I just went back to dual booting win 7/ubuntu 9.1 to using xp in virtualbox, so I'd like to be able to read my ext3 partitions. Thanks!

---

### Post by pythonscript on 2009-10-29
Any ideas from the community? Thanks!

---

### Post by kellemes on 2009-10-29
I assume [this driver]("http://www.fs-driver.org/index.html") should work, they speak of Windows 2008, I guess that's Windows 7.

---

### Post by REDace0 on 2009-10-29
Found this using Google:

[http://www.fs-driver.org](http://www.fs-driver.org)

Looks like it should at least work for ext3. I've personally used a couple different free solutions to this problem a year or so ago and never found one that was really robust. Good luck though!

---

### Post by pythonscript on 2009-10-29
I've used this driver before (under Windows XP) and it worked pretty well, especially considering that the ext3 volume I was reading was actually a "network" drive shared through the NAT controller on virtualbox. Of course, the read/write speed was abysmal... but their Windows 2008 support is new on the website. Maybe they've improved in the year since I've used it. Thanks for the replies!

---

### Post by pythonscript on 2009-10-29
Well, I went to install the driver, and Windows 7 returned an error that the driver was only meant to run on an older version of Windows. I tried it in compatibility mode, but I think I have to restart before it'll actually kick in, if it does.

EDIT:  According to the software developer (I contacted him) this driver *does not *support Windows 7, but support will come "eventually." Thanks for all the help!

---

### Post by BryanFRitt on 2009-11-18
I tried the driver at 
[http://www.fs-driver.org/download/Ext2IFS_1_11a.exe](http://www.fs-driver.org/download/Ext2IFS_1_11a.exe)
using
VirtualBox KUbuntu 8.04 Host Windows 7 Guest, both 64-bit
and got this message
> Ext2 Installable File System 1.11a Setup

This version of the software runs on Windows NT 4.0, Windows 2000, Windows XP, Windows 2003 and Windows Vista (for the x86 and x64 platform) only.

---

### Post by BryanFRitt on 2009-11-18
It seams to work in compatibility mode of Windows Vista (of XP SP2 didn't work)for what little I tested it. Except for the fact that I have to set up the drive letter every Windows 7 boot. I'm curious as to if it's cause I chose SATA for my drive type.

Some other people have said they may have had problems with it:
[http://ubuntuforums.org/showthread.php?t=1031540](http://ubuntuforums.org/showthread.php?t=1031540)

---

### Post by pythonscript on 2009-12-05
I've been having some problems with it as well. When I contacted the developer, he said that a Windows 7 version of the driver was in the works for the distant future. I've worked around my problem with some creative partitioning, though, so that's sufficient for me as of now.

---

### Post by Nokao on 2010-06-12
[http://www.robertbeal.com/528/mount-ext3-in-windows-7-x64](http://www.robertbeal.com/528/mount-ext3-in-windows-7-x64)

---

### Post by landroni on 2010-09-27
Unfortunately i couldnt' install the EXT2IFS on Win 7. 

A less painful solution than described here [1] is to use Total Commander and the ext2+reiser addon [2]. It's GPL-ed, and opens the linux partitions read-only

[1] [http://www.robertbeal.com/528/mount-ext3-in-windows-7-x64](http://www.robertbeal.com/528/mount-ext3-in-windows-7-x64)
[2] [http://www.ghisler.com/plugins.htm#filesys](http://www.ghisler.com/plugins.htm#filesys)

---

