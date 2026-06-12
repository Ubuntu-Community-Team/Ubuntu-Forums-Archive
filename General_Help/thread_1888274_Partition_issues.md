---
title: "Partition issues"
date: 2011-11-28
forum: General Help
---

### Post by nbtbest on 2011-11-28
Hi 

I am trying to run this along with Windows. I partition my hardrive. Can you install this on the other partition. I can try this OS but can not install it on that partition. It just does not give me that option. Also it keeps saying my cd is dirty. Their new cds and i have tryed 3 of them. I want to have the option at start up to either run this or Windows.

thank you 

Val:)

---

### Post by oldfred on 2011-11-28
Welcome to the forums.

Did you burn CD at slowest speed possible? I have never seen it say the CD is dirty? Have you tried cleaning lens on CD drive? There is also a test of CD on the CD menu. Press any key as soon as CD starts with little icons at bottom of screen (rom the cd press any key at accessibility circle and keyboard).


How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html]("http://members.iinet.net.au/%7Eherman546/p27.html")

How many partitions are already in use? Many systems come with all 4 primary partitions used.
Post this from liveCD terminal, if you get it working.
```

sudo fdisk -lu
```

---

### Post by nbtbest on 2011-11-29
Hi thank you for the reply. I have 2 partition. One for my current OS and one for this. Last night I tryed to re-install Ubuntu and it was trying to install on my external hardrive lol. That was my only option. How do I get this to install on my internal hardrives partition?

I'M going to re-burn this useing a ISO software and set it to the slowest burn speed.

---

### Post by oldfred on 2011-11-29
If you have Windows 7, it hides a boot/repair partition and vendors then use another for a recovery or image of your hard drive as purchased. That is how all 4 primary partitions are used even if you only have one or two usable partitions.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Except now use NTFS not FAT for a shared partition:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by nbtbest on 2011-11-29
Hi oldfred thank you for the help. The other day I did a hardrive erase. I wipe the hardrive clean. Then it did a formated. After that I partition the drive into equal 250 gigs. So I put back on the Windows7 OS. It went ok. So now im trying to put on the  	Ubuntu on the other 250gb partition(no dice) This is the error im getting when trying to install Ubuntu.

The installer encounter an error. Copy files to the hardrive or hard disk. Error 5 input/output error.

When I try to install Ubuntu it does not give me the option to install to the new formated/partion 250gb hardrive.

It also says this.
This is often due to a faulty hardisk.And it says it about cleaning the disc. Their new.

---

### Post by oldfred on 2011-11-29
Even a new install of Windows may need a chkdsk. Ubuntu/gparted often will not work with a Windows partition that needs chkdsk. I might try running chkdsk on your Windows partition.

Always run chkdsk and run again until there are no errors, that may be all that is required.
How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by nbtbest on 2011-11-29
Thank you [[COLOR=#d40000]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711")
I keep getting this also.

No root file system is defined.
google is my friend lol:D and you.

---

### Post by oldfred on 2011-11-29
When you use manual install/Something Else you have to choose a partition, specify format & choose what the partition is for. The minimum required partition is / (root). You should create swap (no format) & often best to create a separate /home each in separate partitions.

---

### Post by nbtbest on 2011-11-29
Ok did the install useing the 
**Download Ubuntu installer for Windows**

Even though it took 3 times. The first 2 times it frozed at copy the files. But the 3rd was the charm.
There is going to be some learning curve. So be it. This was installed on a 3 year old computer bought new. Now its just used for software experimentation.

I plan on putting this  				[Ubuntu]("http://ubuntuforums.org/index.php") OS on a new computer build(thats what i do). But so far it looks nice. Thank you so much for the help.:)
[B]
[/B]

**[**]("http://www.google.com/url?sa=t&rct=j&q=experimentation&source=web&cd=2&ved=0CEEQFjAB&url=http%3A%2F%2Fwww.thefreedictionary.com%2Fexperimentation&ei=mXfVTs6hKoqtsALDypGIDw&usg=AFQjCNHn0S8JJQ23t66JOVsDwoqmJ7tYZA&cad=rja")**

.

---

### Post by oldfred on 2011-11-29
You have installed wubi, which if good for an extended test of Ubuntu. It runs as the full Ubuntu but is just a file inside the Windows NTFS partition and uses the Windows boot loader in the MBR.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

But even the developer of wubi thinks you may want to convert to a full partitioned install:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Someday you may want these:
Uninstall wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

