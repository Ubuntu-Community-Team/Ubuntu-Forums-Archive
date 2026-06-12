---
title: "Planning a new install and repartition, would like advice"
date: 2011-12-09
forum: General Help
---

### Post by x C0MMAND0 x on 2011-12-09
Here's the short of it.  I currently have Windows 7 and Ubuntu 10.10 setup as a dual boot system.  I want to do a NEW install of Ubuntu 11.10, but also at the same time make it so my root and home are on separate partitions.  I have everything completely imaged and backed up, so I am not worried about data loss at all, I just need to know the best way to separate partitions out.

Please see the attached screenshot of my current partitioning. I don't know what sda1 is, but sda2 is Win7.

when I install Ubuntu 11.10 overwriting 10.10. I need this to do a manual partitioning and set it up so that my /home is separate from my / and my swap.

I am wondering what the best way to do the custom partitions is.  During the install, I know if gives the option to choose a custom install, and I will be able to leave Windows where it is, but then I need to set up my home and root partitions.

Question 1 - Between the following 3 partitions, home, root, and swap, does it matter what order on the disk they are?  I was thinking of doing the root partition, then home, then swap

Question 2 - In the custom installer, I see that I can set a mount as "/" or "/home", but I don't see how to create the swap.  Is it automatically created?

---

### Post by x C0MMAND0 x on 2011-12-09
*More info*

I stumbled upon this link [http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/") which seemed to have good information.  Here is my thoughts for how my system might look when I'm done.

/sda1 ntfs   System Reserved   100Mb
/sda2 ntfs   Windows 7         100Gb

/sda3 **ext?**   /boot             500Mb
/sda4 SWAP   SWAP              **?????**
/sda5 /      ROOT              30Gb
/sda6 /home  HOME              Remaining Space

Should I make /boot, / and /home all Primary or logical?  I don't know the difference.  How big should I make my swap?  I have 4GB of memory in my laptop, and I will be running a 64bit install.  What file system should I use for the /boot partition?

---

### Post by dabl on 2011-12-09
Just leave your first 3 partitions as-is, since nothing that you want to do requires any change to them.

Within the extended partition, what you want to do is (assuming you are done with the Ubuntu 10.10 OS) shrink the /dev/sda5 partition down to something on the order of 15GB.  That will leave an unallocated space before the swap partition.  In the unallocated space, make a new ext4 partition.  That will become the new /dev/sda6, and the swap partition will become /dev/sda7.

When you install the 11.10, the OS root goes in /dev/sda5, and /home goes on /dev/sda6. It will automatically find the swap partition.

Two more issues:

The hazard warning on the Win 7 partition is not confidence-inspiring -- better chkdsk it asap.

Your swap partition is twice as large as it will likely need to be.  You could shrink it to 4GB, unless you're editing huge videos or doing some extremely fancy graphics work.

---

### Post by Lars Noodén on 2011-12-09
> **x C0MMAND0 x said:**
> 

Question 1 - Between the following 3 partitions, home, root, and swap, does it matter what order on the disk they are?  I was thinking of doing the root partition, then home, then swap

Question 2 - In the custom installer, I see that I can set a mount as "/" or "/home", but I don't see how to create the swap.  Is it automatically created?

1) The order does not matter at all.

2) You'll see the mount point option only if you specify a file system like EXT4.  Set the file system type for swap, it's one of the options.

---

### Post by x C0MMAND0 x on 2011-12-09
Okay that makes sense...Since I have 4Gb of RAM do I really need an 8Gb swap?  That seems quite large, and I guess I don't really understand what the swap partition does anyways.

And from what I'm understanding, I don't need to have a separate /boot partition?

---

### Post by Lars Noodén on 2011-12-09
A separate /boot partition is not needed.  

The swap is there in case you run out of RAM.  I've looked around for material on how to calculate [swap size](http://www.google.com/search?q=swap+size) and the consensus seems to be that there is no consensus.  However, with the gigantic amounts of RAM available nowadays the old rule of thumb (2x RAM) no longer applies.  I've read some arguments saying that it need not exceed 4GB.  I've set mine to 2GB on systems with 4GB of RAM and not run into any trouble.  (If unscientific anecdotal evidence is needed.) swap can also be added later as a swap file and not a separate partition, should the need arise.

---

### Post by x C0MMAND0 x on 2011-12-09
Awesome, thank you so much for the help.  I will document my process as I work on this over the weekend, and post it here for others.  I know there are lots of dual-boot users who might be interested in upgrading and separating there /home partition at the same time.

One last question (I think).  What is the difference between a primary and logical partition?  I looked around online but I couldn't find a "simple" answer that gave a more conceptual understanding.  When creating the different partitions between root, /home and swap does it matter if I set them as primary or logical?  I know you can only have a max of 4 primary partitions, but that honestly means nothing to me.

Thanks again for everything so far.

---

### Post by dFlyer on 2011-12-09
You shouldn't need a separate boot partition these days. My advice is a 15-20 gig / partition, 8 gig swap if its a laptop and you let your computer sleep and the rest to your /home partition.

---

### Post by dabl on 2011-12-09
> **x C0MMAND0 x said:**
> 

One last question (I think).  What is the difference between a primary and logical partition?  I looked around online but I couldn't find a "simple" answer that gave a more conceptual understanding.  

Simple answer:  You are limited to 4 primary partitions, but if you use one of those 4 for an extended partition, then inside that you can have a larger number of additional logical partitions, and Linux (as opposed to Windows) is happy to live and do its business from logical partitions.

More complete answer:  [http://tldp.org/HOWTO/Partition/partition-types.html](http://tldp.org/HOWTO/Partition/partition-types.html)

---

### Post by LewisTM on 2011-12-09
A boot partition would only be useful if you want to play around with advanced filesystems like xfs or btrfs, which don't boot well.
It would be formatted as ext2 and take up no more than 256 mb.

You can only have 4 primary partitions on a given HDD. One of them can be marked as active and would be bootable. Another can be set as extended and become a russian doll with any number of logical partitions inside. GRUB, the Linux boot manager, can sit in the master boot record outside of the partition table and set to boot any partition, even logical ones.

For simplicity, I would just stick to the scheme proposed by dFlyer. Personally I formatted my /home to xfs because I find it's more reliable and just as fast as ext4.

---

### Post by oldfred on 2011-12-09
What partitioning is best is very personal, but even my own "best" partitioning scheme is not so good a couple of years later. What I want to do  has changed. But by then I assume hard drive is getting older, new drive will be larger and I can start all over.

I would suggest two additional things. One make sure you have a Windows repairCD and if using Windows create a shared NTFS partition for any data you may want in both systems.

The sda1 100MB partition is Windows boot/repair partition. If you can start to boot you can often get to the repair console, but if you cannot boot then you need the Windows repairCD.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I used a shared NTFS partition for my dual boot with XP when I used XP. I had Firefox & Thunderbird profiles, photos & some data in it, so all that was accessibility from both Windows & Linux. To avoid issues with Windows it is best to set the c: drive as read only in Linux and only use the shared partition as read/write. If not using Windows much anymore then you may not need a shared NTFS partition. It can be a logical as Windows reads logicals fine, but has to have a primary to boot from.

---

### Post by Lars Noodén on 2011-12-09
> **x C0MMAND0 x said:**
>  What is the difference between a primary and logical partition?  I looked around online but I couldn't find a "simple" answer that gave a more conceptual understanding.  When creating the different partitions between root, /home and swap does it matter if I set them as primary or logical? .

I've looked around for an authoritative source on the differences and cannot find anything.   It has something to do with being a holdover from the very early days of personal computers.  A textbook on operating systems might have a description of the two, that's where I last saw anything useful on the topic.  

I can't remember the difference because in the context of Linux it does not matter if the partitions are logical or physical.  You can choose either or both for your setup.

---

### Post by oldfred on 2011-12-09
LewisTM covered the main difference between primary & logical.

Some more info if interested.

[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Just for future info. Brand new systems do not use BIOS & MBR(msdos) which has been the standard since the IBM PC was released with a hard drive in the early 1980's. New system now have UEFI but many vendors are still calling it BIOS and the partitioning is gpt(GUID). Only new versions of Windows work with UEFI and grub is still a work in progress with UEFI.

---

### Post by larrypg on 2011-12-09
Hello,

You do not make your sda3 /, /home, or /boot.  It is more or less a container for the logical partitions which will start on sda5 (there will not be an sda4).  Use gparted to shrink sda5 and make the unallocated part your ext4 /home.  Probably repeating what others have said but it does not hurt to say it again.

---

