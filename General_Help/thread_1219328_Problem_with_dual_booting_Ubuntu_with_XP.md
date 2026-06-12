---
title: "Problem with dual booting Ubuntu with XP"
date: 2009-07-21
forum: General Help
---

### Post by Ranek on 2009-07-21
Hey all, I wondered if you could help me with a problem.

I've had two Hard Disks installed in my computer. One was running Windows XP, and the other was running Windows 7 Beta. At this point everything was working fine, but I just recently installed Ubuntu on my second disk, and since then my second disk no longer appears in My Computer on XP. It has no Drive letter in Disk Management and appears as "Status: Healthy (Unknown Partition)". I can right click on the disk, but the only option I recieve is deleting the partition which I don't want to do.

There must be some way around this, when running Ubuntu I can access both my hard disks, but not on Windows, which I find a bit odd. I've googled this problem but haven't made much progress so wondered if anyone here could lend a hand. I'm not entirely sure if this is a problem being caused by XP, or one that was caused by my installation of Ubuntu.

If anyone can shed any light on this i'd really apreciate it.

I've included a print screen to show how my Disk Management looks.

[http://i31.tinypic.com/2dawrid.jpg](http://i31.tinypic.com/2dawrid.jpg)

Thanks

Chris

---

### Post by Cyked on 2009-07-21
It looks like from the screen cap you partitioned 5.79gb for Ubuntu?

Can you boot to Ubuntu?  If so can you then mount the partition and other drive and read them?

---

### Post by Ranek on 2009-07-21
When installing Ubuntu I used the guided install so I didn't actually set any partition sizes myself, it did it all for me.

---

### Post by Cyked on 2009-07-21
> **Ranek said:**
> When installing Ubuntu I used the guided install so I didn't actually set any partition sizes myself, it did it all for me.

So when you did the install when you got to "where" to install you selected something along the lines of using available disk space on drive 2?

---

### Post by confused57 on 2009-07-21
You could try installing fs-driver in XP:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Ranek on 2009-07-21
> **Cyked said:**
> So when you did the install when you got to "where" to install you selected something along the lines of using available disk space on drive 2?

I selected the second drive which currently had windows 7 on. The drive was completely formatted and then Ubuntu was installed.

And yes I can boot to Ubuntu and I can enter and view files on all my Hard Disks. Which is why I find the whole thing pretty strange :D

I'll try the driver the poster below posted, and fill you in with my findings. 

Edit: Ok, I tested the drivers, and they appear to have worked. I can now see the 2 partitions in Disk management with drive letters, and the 2 partitions now appear in My Computer. But when trying to open one it says that it needs to be formatted. Any idea what the problem is there? The disk was formatted on installation, it shouldn't need to be formatted again should it?


Another link here to show the problem: [http://i29.tinypic.com/35luv77.jpg](http://i29.tinypic.com/35luv77.jpg)

Thanks

Chris

---

### Post by Ranek on 2009-07-21
I used the moundiag.exe program from the website and recieved these messages, but not too sure how to proceed:

> Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Chris\My Documents>mountdiag L:
The volume has not been mounted. No file system has been recognized.
You may look at the /etc/fstab file of your Linux installation to get more
information.

C:\Documents and Settings\Chris\My Documents>mountdiag K:
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because the file system has an inode size unequal to 128 bytes (inode
size: 256 bytes).
The only way to solve it is to back up the volume's files and format the file
system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all
backed-up files.
After that, the Ext2 IFS software should be able to access the volume.

C:\Documents and Settings\Chris\My Documents>

---

### Post by Cyked on 2009-07-22
What did you format the drive as when you did the Ubuntu install?  You can't access it or see it previously because Windows can't natively read Ext3 or whatever you formatted as (Ext2?).  Did you have the drive partitioned in 2 parts before the Ubuntu install?  Looks like you have 2 partitions, one at 5.79gb and one as 143gb (or whatever the exact sizes).

I don't know about the mountdiag.exe program.  Did you also go to the FAQ on the fs-driver site regarding Ext3 filesystems?

[http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

---

### Post by Ranek on 2009-07-22
> **Cyked said:**
> What did you format the drive as when you did the Ubuntu install?  You can't access it or see it previously because Windows can't natively read Ext3 or whatever you formatted as (Ext2?).  Did you have the drive partitioned in 2 parts before the Ubuntu install?  Looks like you have 2 partitions, one at 5.79gb and one as 143gb (or whatever the exact sizes).

I don't know about the mountdiag.exe program.  Did you also go to the FAQ on the fs-driver site regarding Ext3 filesystems?

[http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

When I formatted the drive I wasn't given any options as to what I was doing. I assume thats the purpose of the guided install, for novices to Linux such as myself to install without having to deal with things we currently don't understand :D

The drive was in two partitions before the install, but the format used the entire disk so I assumed it would delete both partitions and install on just one. But I'm guessing the smaller 5.6gb partition is where the filesystem is, to keep it seperated.

From the message I recieved its obvious my problem is something to do with this:

> What features are *not* supported?

    * Inodes that are larger than 128 bytes are not supported.

And my Inode is 256 bytes. Thats where my problem occurs, but this is something that I have no idea how to change, or even if its possible.

Does anyone know how to change this?

---

### Post by Scarlath on 2009-07-22
By the looks of it. Both K: and L: are Linux partitions seeing as it says "Unknown Partition". Perhaps you could post your partition manager from Ubuntu instead? That way we could know for sure how your computer was set up (you can use *sudo fdisk -l* (lower case L))

As far as I know, the guided installation chooses Ext3 as file system. As you've already been told, Windows cannot read Ext3 without the use of additional software... this is what Fs-driver enables you to do. Not sure why exactly it wouldn't work for you though, did you download it from this link: [http://www.fs-driver.org/download/Ext2IFS_1_11a.exe](http://www.fs-driver.org/download/Ext2IFS_1_11a.exe) ?

Mountdiag is just a diagnostics tool.

Perhaps try restarting your computer?

---

### Post by Ranek on 2009-07-22
Hey again

Doing a bit of searching I came across this thread:

[http://ubuntuforums.org/showthread.php?t=979523](http://ubuntuforums.org/showthread.php?t=979523)

After a bit of reading I realised I had two options, I could either reinstall part of Ubuntu or try another tool.

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

Which is supposed to work with a 256k inode.

I uninstalled the Ext2 IFS and installed Ext2FSD and now its all working super. I'm able to both read and write onto the Ext3 file system. I've left the swap partition untouched but now I can use the other 112Gb while on Windows aswell.

Thanks for everyones help.

No doubt you'll see me again in the future! Probably when I start setting my wireless netowrk using the ndiswrapper :D

---

### Post by confused57 on 2009-07-22
Thanks for the info, I'm using Hardy 8.04, so wasn't aware
of the 128k vs 256k inode issue.  Filed for future reference.

---

