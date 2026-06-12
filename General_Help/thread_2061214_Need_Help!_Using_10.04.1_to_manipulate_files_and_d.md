---
title: "Need Help! Using 10.04.1 to manipulate files and drivers in Windows file systems!"
date: 2012-09-22
forum: General Help
---

### Post by xovertheyearsx on 2012-09-22
***General Introduction***
I've come across an interesting issue that seems to be very common with little to no information regarding how to solve it. 

If there is a solution, it's usually quite curt and almost always seems to exclude certain, useful, descriptions that could help the general public for general software repair issues.

I've searched Google for a good 3 or 4 hours now and I'm tired of searching through the same old threads.

I popped out my Ubuntu Iso and popped it in to a Windows 7 Dell Inspiron using a Intel Pentium Dual Core Processor.

***Background Information***
Now, before I get started, there are a few things to note here.

I've already gone through the normal routine before deciding to resort to this methodology.

- Windows fails to load and it hangs
- Run Windows Repair Mode
- Run Safe Mode
- Run Safe Mode w/ Command Prompt
- Run Repair Service Utility
- Boot from Windows DVD and run System Restore
- Boot from Windows DVD and run Repair

All of the above seem to just "*hang*" before, during, or after the windows logo appears.

***The General Idea***
I used Ubuntu for about 2 - 3 years and loved what it could do. Sadly, it's mainly a developmental environment. At the same time it's an OS I love to use.

So I decided why not give Ubuntu a run and see if it can load the ISO.

Viola! It loaded. I'm writing this thread using the Live OS.

Now the goal is to _**m**_ount the Windows 7 file-system in Ubuntu and replace one file: classpnp.sys (c:\windows\system32\drivers\classpnp.sys)

I know Ubuntu can somehow mount and load the NTFS file-system and read and write files because I've done it on multiple occasions with XP, WinVista, and Win7.

***So What's the Problem?***
The problem is figuring out how to mount a Corrupt Disk Partition in Ubuntu. Ubuntu even tells me that the NTFS Partition is Corrupt.

So the first thing I try to do is go to *Places > FileSystem* and it reads back an error. Can't Mount the file system.

So I go to *Applications > Accessories > Terminal* and I type

> 
fdisk -l

*Output:*

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6bec776c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023f15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121598   976728064    7  HPFS/NTFS
So I say to my self, okay, all I have to do is mount the file system.

> 
sudo mkdir /media/win7

sudo mount -t ntfs /dev/sda1 /media/win7

*Output:*
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Now, I know the HDD is not a RAID because it's a Basic Laptop. 

I obviously can't run *_**c**_hkdsk /f* because Windows just hangs when I attempt to do anything to it.

And all the other forums (sevenforums included) are all absolutely useless for such a common problem. 
I obviously can't unplug my keyboard and mouse :lolflag:
We'll I could, but why should I have to take apart my laptop to unplug a few bands from the motherboard? (One of the many reasons why Linux is amazing! We don't have to put up with that crap.)

I know I could wipe the partition and start from scratch, but I have files for school on it and I need them ASAP! I can't afford to go to the PC shop and I know that's what those damn Geek Squad members will pull on me.

So I'm hoping I can get some help and this will just be even more proof why Linux is the OS to choose from. Even in the IT world. I know Linux has a way to get in to this HDD. 

So Please Help Me and Thanks to anyone that does.

---

### Post by oldfred on 2012-09-22
Chkdsk from Windows is always the first and best thing to run.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

You can force mount partitions with errors, but then you are responsible for any corruption.

I guess I am out of date

From 
man ntfs-3g

> force  This option is obsolete. It has been superseded by  the  recover
              and norecover options.


---

### Post by xovertheyearsx on 2012-09-22
> **oldfred said:**
> 
Chkdsk from Windows is always the first and best thing to run.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

You can force mount partitions with errors, but then you are responsible for any corruption.

I guess I am out of date

From 
man ntfs-3g


Thanks for the fast reply!

> 
"I obviously can't run chkdsk /f because Windows just hangs when I attempt to do anything to it."


^ This really was the first thing I attempted to do, but I can't access it :(

I haven't heard of Test Disk before so I will definitely give it a try.

I've also been attempting to run ***_n_**tfs-3g* instead of ***_m_**ount* but they both spew out the same error.

Also, the disk is already corrupted and I had already considered a force mount but I was hoping for a more elegant methodology.

**Just an FYI, the laptop was already sent out to the manufacturer and they returned it saying that it is NOT a hardware issue, it's purely software.**

---

