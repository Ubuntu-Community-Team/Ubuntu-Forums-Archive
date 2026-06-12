---
title: "Help with drive recovery"
date: 2011-08-14
forum: General Help
---

### Post by gaurish108 on 2011-08-14
Hello I have been running Ubuntu 10.10 on my Hitachi 500 GB hard drive. No Windows on my computer at all. This hard disk had developed some bad sectors in the past few months.  

Two days my after a power supply cut, I openend up my computer to see that ubuntu was not booting 
and there was some gibberish on the screen leading to a terminal prompt labelled 'initrafms'

As I type this I am using the Ubuntu live CD. Can anyone guide me on how to do data recovery. Many of 
the tutorials online assume the data is being recovered from Windows partition which is not really useful for me here. 

After clicking on Places--->488GB filesystem I am getting the following message in a window 

Unable to mount 488GB filesystem:
A job is pending on /dev/sda1


Can any one help me out please? Here is some information I get after *fdisk -l* and *blkid.* 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057b64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59272   476097536   83  Linux
/dev/sda2           59272       60802    12285953    5  Extended
/dev/sda5           59272       60802    12285952   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 

```

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="acbb0dc4-e9dd-468d-b243-d269eb04db74" TYPE="ext4" 
/dev/sda5: UUID="81370ae0-6002-42f7-8301-7807f0ba1b73" TYPE="swap" 
```

---

