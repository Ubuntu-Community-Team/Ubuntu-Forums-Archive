---
title: "Ubuntu installation problem/recovery of data!"
date: 2011-10-20
forum: General Help
---

### Post by zachiechan on 2011-10-20
Hi. I recently installed Ubuntu on my computer. I burned it to a disk, installed it on my computer. i wanted to test it out to see if i liked it. But i want to change back to windows 7 but when I start my computer it doesnt give me that option. When I installed it never gave me the option to install alongside windows 7. I believe I paritioned Ubuntu on my entire disk and didn't reserve any for windows 7.  Can anyone tell me what I did wrong or how to recover all my programs and files on windows 7? Please help!!! Thanks!

---

### Post by nothingspecial on 2011-10-20
When you open a terminal and type

```
sudo fdisk -l
```

What does it say?

---

### Post by zachiechan on 2011-10-20
It says:


[sudo] password for zachmah:

---

### Post by nothingspecial on 2011-10-20
> **zachiechan said:**
> It says:


[sudo] password for zachmah:

Type your password (you won't see it) and hit Enter.

Then what does it say.

---

### Post by zachiechan on 2011-10-20
Typed my password and got this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00071093

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968574975   484286464   83  Linux
/dev/sda2       968577022   976771071     4097025    5  Extended
/dev/sda5       968577024   976771071     4097024   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 4195 MB, 4195352576 bytes
255 heads, 63 sectors/track, 510 cylinders, total 8194048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb1cef758

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
zachmah@ubuntu:~$

---

### Post by nothingspecial on 2011-10-20
Well you are right, Windows has gone.

It is possible you may have some success with [testdisk]("http://www.cgsecurity.org/wiki/TestDisk")

But other than trying some windows recovery tools (with which I am unfamiliar) your programs and files are gone.

Perhaps someone else may give you a second opinion.

---

### Post by zachiechan on 2011-10-20
Oh ok thanks for the help! I will see what this testdisk does. Anymore help from anyone please?

---

### Post by zachiechan on 2011-10-20
Sorry but how do you use and download test disk? I have looked on there website and I do not understand because I now have Ubuntu. Also can anyone reccomend any data recovery software or anything? Thanks!

---

