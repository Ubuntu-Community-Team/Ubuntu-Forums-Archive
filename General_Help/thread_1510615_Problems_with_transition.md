---
title: "Problems with transition"
date: 2010-06-15
forum: General Help
---

### Post by Krolblach on 2010-06-15
Hi all,

Only just found out about Ubuntu and loving what I'm seeing so far. I've installed the OS on my computer (currently running windows XP) and am having a few problems. My hard drive is partitioned. I have the normal C drive, which only has 16g max space, and the partition drive: S, which has the majority of my files and programs on as it has 216g max space! After installing Ubuntu I was dismayed to find that the S drive is nowhere to be found and that the system therefore cannot find any of my major applications or files, including my wireless internet connector. I also only have access to 16g of space, much of which is already taken up. As this means I am without a paddle in every way when loading up Ubuntu, I was hoping someone could help me out a bit! How can I help Ubuntu find my partition drive, or can someone tell me how to un-partition it, as I have tried without success to do this as well.
Really looking forward to getting used to Ubuntu, but until I get this sorted, I'm screwed.
Hope someone can help!
Cheers,
Krolblach

---

### Post by bodhi.zazen on 2010-06-15
First, welcome.

Second, Linux refers to partitions with different syntax :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

Open a terminal and enter:

```
sudo fdisk -l
```

Or install gparted

```
sudo apt-get install gparted
```

gparted is graphical.

Either copy and paste the output of the above command or a screenshot of gparted.

---

### Post by oracle2b on 2010-06-15
run in the terminal: sudo fdisk -l

what do you see?

---

### Post by Krolblach on 2010-06-16
Thanks for the quick responses :P
After typing in "sudo fdisk -l" I see:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x14d814d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2219    16775608+   7  HPFS/NTFS
/dev/sda2            2220       32301   227419920    7  HPFS/NTFS

When I opened up the disk utility I saw both partitions and saw the option to delete partition, but am not sure whether this will also delete all the data on my partition. 

I tried running the command " sudo apt-get install gparted" but it came up with :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gparted

Any thoughts?

Krol

---

### Post by bodhi.zazen on 2010-06-16
Are you using wubi ?

---

### Post by Krolblach on 2010-06-16
Yes I am. Does this mean lots of things are different?

---

### Post by 3rdalbum on 2010-06-16
Right now you're using Wubi, which installs an instance of Ubuntu within a file on a Windows partition. This isn't really the best way of doing it because of a couple of reasons, including the one that you're posting about. (lack of space, confusion about where your disks are, inability to boot into Ubuntu if you can't boot into Windows, etc)

I'd advise that you remove Ubuntu using Windows' Add/Remove Programs function, and then actually boot up Ubuntu from the CD. You'll be asked if you want to try Ubuntu from CD or install it; you want to install it. You'll be given some options for partitioning one of your disks and install Ubuntu side-by-side with Windows. When you're done and booted into your newly-installed system, you'll be able to access all drives, and Ubuntu will be completely independent from Windows.

---

### Post by Krolblach on 2010-06-16
Fantastic advice, thank you!
As I downloaded Wubi online, how would I go about putting Ubuntu on a CD? Would I put a disk in the drive and download it straight there? Also, would this have to be a DVD because of the download size?
Cheers,
Krol

---

### Post by bodhi.zazen on 2010-06-16
> **Krolblach said:**
> Fantastic advice, thank you!
As I downloaded Wubi online, how would I go about putting Ubuntu on a CD? Would I put a disk in the drive and download it straight there? Also, would this have to be a DVD because of the download size?
Cheers,
Krol

wubi in intended as a "trial", if you wish to stay with Ubuntu I suggest you do a standard install for exactly these issues.

Download the Ubuntu Desktop CD.

See :

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Krolblach on 2010-06-16
Solved!
I burned a CD and the OS is now working fine and I can see all my drives. Thanks for the help, everyone!
Now I just have to work out how to get my Windows apps to work... :P

---

