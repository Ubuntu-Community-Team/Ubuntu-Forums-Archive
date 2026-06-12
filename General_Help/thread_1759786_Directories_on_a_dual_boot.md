---
title: "Directories on a dual boot"
date: 2011-05-16
forum: General Help
---

### Post by otacon507 on 2011-05-16
I was looking to start a dual boot and was inquiring to see if I can download files from the Windows 7 boot and direct it to the Ubuntu partition/home directory.  Thanks
-J

---

### Post by Phil Stone on 2011-05-16
Windows doesn't 'see' linux os partitions as they are of a different format type. You will find it easier to download in windows then once you boot into linux move or copy the files across from windows as  the ntfs filesystem windows uses can be accessed more easily from linux. 

Though there are tools such as ms tools for use when in windows to transfer into the linux partitions. But essentially you can transfer files from one filesytem to another.


also see thread: [http://ubuntuforums.org/showthread.php?t=1759041](http://ubuntuforums.org/showthread.php?t=1759041)

original reply:
boot loaders such as grub will generate the partition info when they are installed so you shouldn't need to load the windows 7 master boot  record (mbr) information across. you will be able to select which os to boot into once you have installed the ubuntu on a secondary partition and start the pc up.

---

### Post by deathadder on 2011-05-16
As pointed out, Windows doesn't understand the file systems used by Linux. I've had some limited success with a [EXT2/3 driver for Windows]("http://www.fs-driver.org/") but still find the easiest way to transfer files is using a drive with FAT32 on it...usually my external driver.

---

### Post by seawolf167 on 2011-05-16
As posted, Windows doesn't understand ext formatted partitions. Ubuntu w/linux however, can read/write to NTFS so you can transfer the files from your download location in Windows to Ubuntu while booted in Ubuntu.

[Here ]("https://help.ubuntu.com/community/WindowsDualBoot")is a dual boot guide for how to setup your computer depending on which OS you install first.

---

