---
title: "Partitioning and Dual Boot"
date: 2012-08-29
forum: General Help
---

### Post by webmanoffesto on 2012-08-29
I have a new Asus laptop with 500GB HD, 4 GB RAM. I want to  dual boot Windows and Ubuntu on it. How do you suggest I partition it.

Maybe:
Windows partition (how large?)
Swap 4GB (or should that be 8GB, that is 2xRAM?)
Root 5-10 GB
Home (Data?) the remaining disk space (Both Windows 7 and Linux can access files. NTFS folder?) 

And  how much space does a normal Windows partition need (Windows  Enterprise, Office 2007, plus a few more programs, probably not many  programs because I have lots of programs as "portable" on my USB  DiskOnKey.

Note: I find the whole extended partition thing SO  confusing (primary, extended, and logical). I just never manage to  understand it.

Important I want my data to be accessible both  from Windows and from Linux. I guess that means Data will be a shared  NTFS partition.

---

### Post by Comodín on 2012-08-29
I would make your Windows partition not too small, something like 50 Gb would be more than enough and you can still install programs in the future and expand. But minimum would be 26 GBI found [this page]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") very helpful and easy to follow. He also gives another solution for the swap, no partition but storing it in a file on the Ubuntu partition.

I hope it helps.

---

### Post by Megaptera on 2012-08-29
Loads of good info on partitioning with helpful screenshots: [http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning](http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning)

Loads of info on dual booting again with lots of helpful screenshots: [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

I found screenshots helpful when looking at partitioning - hope these of use?

---

### Post by Mark Phelps on 2012-08-29
BEFORE you start messing around with repartitionig, strongly suggest you read the following ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by oldfred on 2012-08-29
/home cannot be NTFS. 

I do prefer smaller system partitions Windows & / and larger data partitions. Use NTFS for shared data. If putting most of your data into the shared NTFS data you may not need a separate /home. I moved /home back into / and had a shared NTFS and as I stopped using XP created a ext3 (I would use ext4 now) data partition and use the shared less.

I might suggest Windows at 30 to 50GB, Ubuntu 25GB, swap at 2GB if you have more than 3GB of RAM or swap at the same size as RAM in GiB if you want to hibernate. Use the rest for NTFS shared data and maybe separate /home or data partitions.

---

### Post by webmanoffesto on 2012-09-01
Thanks for all the great information.

Another question
And when I boot up this laptop off of an Ubuntu Live Disk
I only see /dev/sda = 465.76 GiB, with all that space &quot;unallocated&quot;
That doesn't make sense to me. I should see at least a recovery partition and &quot;the rest&quot;
or: Recovery, Data, and OS  Edit: Here is how the partitions look when I boot into Windows 7 and use the Manage Disks [IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/AsusLaptopDiskManagementPartitionsDiskPartitionsv20120901n01.png[/IMG]

---

### Post by roger_1960 on 2012-09-01
Hi there

I understand your confusion.  You have some good answers above.  Post #4 is very important!  You do have 4 primary partitions on Disk0 (partitions are primary or extended or logical and it would say if they were the latter 2 types)and cannot install Ubuntu without sorting that out.  My suggestion is:

Using Win7, delete the Data (D) partition. (Its empty and this gives you unused space and only 3 primary partitions left)

Using Win 7, shrink the windows OS C: partition to say 100GB.  Its already got 56GB in it, so 50 isn't enough!)

Now you can use Ubuntu install disk to create an extended partition in the empty space.  An extended partition is like a container holding Logical partitions.  (In itself an extended partition does not hold data, just partitions.  Its like the outer box you get when ordering from Amazon - nothing in it but other boxes)Within the extended partition you can create all the new partitions you want, using the "something else" option as suggested by others above.

I would physically unplug your external drives while doing any of this so you can't accidentally format over your data!

I'm not sure why you can't see the partitions from the Ubuntu disk.  Is the md5 sum OK?  Have you tried looking at it with a gparted live disk?

Hope this helps a little.

---

### Post by oldfred on 2012-09-01
+1 on roger_1960 suggestions.

I also prefer smaller system partition and put data into shared data partitions, so you are not directly writing into the Windows system from Ubuntu. You can easily recreate the NTFS partition in the extended partition. Windows & Ubuntu can then both read & write to that partition. 

I used my shared NTFS for Firefox & Thunderbird profiles & all photos as we used the Windows version of Picasa in both XP & Ubuntu (.wine).

---

### Post by gordintoronto on 2012-09-01
Here's a specific suggestion:
 - make DVDs from the recovery partition, make copies of the DVDs, then get rid of the partition,
 - Expand the Data partition to use the space from above,
 - defrag C: then shrink it, using the Windows tool described above,
 - if it didn't shrink by at least 10 GB, stop! You will need to take a different approach.
 - Run Gparted from a live CD or USB. Make the space created by shrinking into an ext4 partition and format it.
 - install Ubuntu. As suggested above, use the "something else" manual partitioning feature. Select the ext4 partition as root (/) and the Data partition as /home. Make sure they are both set to DO NOT FORMAT.

Sorry, you also need to figure out what to do about Grub. Ask Oldfred for advice about it.

---

### Post by oldfred on 2012-09-01
I just noticed that Windows is showing the first partition as efi.

That changes a lot of things. Both Windows and Ubuntu have to be installed in BIOS/MBR or UEFI/gpt modes. When booting a 64bit liveCD you should get two choices on booting - UEFI/efi and BIOS/legacy/AHCI or whatever your system calls it.

So is system UEFI.

Post this from liveCD.

sudo parted /dev/sda unit s print

If first partition is efi and drive is partitioned with gpt then Windows is in UEFI mode.

---

### Post by YannBuntu on 2012-09-04
Hello
Please also indicate your Boot-Info URL. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by webmanoffesto on 2013-02-27
I dropped this project for a while, I'm now just getting back to it

```
sudo parted /dev/sda unit s print
```Gives me
```
Model: Unknown (unknown)
Disk /dev/sda1: 409600s
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End      Size     File system  Flags
 1      0s     409599s  409600s  fat32

```What does that mean?

> **oldfred said:**
> I just noticed that Windows is showing the first partition as efi.

That changes a lot of things. Both Windows and Ubuntu have to be installed in BIOS/MBR or UEFI/gpt modes. When booting a 64bit liveCD you should get two choices on booting - UEFI/efi and BIOS/legacy/AHCI or whatever your system calls it.

So is system UEFI.

Post this from liveCD.

sudo parted /dev/sda unit s print

If first partition is efi and drive is partitioned with gpt then Windows is in UEFI mode.

> **YannBuntu said:**
> Hello
Please also indicate your Boot-Info URL. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Nice Program. Here's the URL [http://paste.ubuntu.com/5570419/](http://paste.ubuntu.com/5570419/)

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

 __________________________________________________________________________

---

### Post by oldfred on 2013-02-27
Your post #12 is only showing the flash drive as sda, but Boot-Repair showed main hard drive as sda. Some systems may mount flash as sda.

Have you backed up your Windows partition and the efi partition?  Must do this.
Have you made a Windows repair flash drive.

Have you used Windows to shrink the Windows partition, but not to create new partitions? ReBoot Windows several times to make sure it runs chkdsk and makes whatever repairs it wants based on new size.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
Other Asus installs and various issues they had.
       Asus N56VJ-SH71-CD Shows default Windows partitons Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

            ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by webmanoffesto on 2013-03-01
Wow, this is getting complicated.  
Maybe I should just format the whole drive, and start from scratch.   
- Format all   
- Create partitions for Data, Ubuntu, Windows and begin by installing Windows   

I have my data backed up I have the EFI partition backed up (is that the recovery partition?)  
I have a W7 rescue CD I made a W7 install-from-USB DiskOnKey  
I also have a USB DiskOnKey with Yummi MultiBoot with a few distros and recue disks.

---

### Post by oldfred on 2013-03-01
Somewhere I read the Windows was not offering new drivers for Windows 7 to use with any new hardware offered with Windows 8. So your Windows 7 may not work.

Windows 7 may install in non-secure boot mode but will not ever work with secure boot.

---

