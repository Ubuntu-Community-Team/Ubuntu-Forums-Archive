---
title: "Windows 7 and Ubuntu not recognizing each other's partitions"
date: 2011-12-24
forum: General Help
---

### Post by aepokh on 2011-12-24
I've been trying for a few days now to dual-boot Windows 7 and Ubuntu 11.10 (both 64-bit) on my Asus U52F laptop. Whichever order I install them in, the second OS installer either won't see or will actively ignore the installation made by the first OS.

When I install Ubuntu or some other Linux distro first, Windows will complain that it can't install on my hard disk because the partitions are GPT-style or some such. It won't even let me make a new partition in the unallocated space; the only option is to delete and repartition the entire disk.

When I install Windows 7 first, Ubuntu won't recognize that the partition I installed Windows on even exists. Again, the only option is to repartition the entire disk. Fedora and GParted live boots are much the same way.

I've looked at numerous tutorials for dual-booting Windows 7 and Ubuntu, and none of them describe any such behavior. I searched this forum and others for and similar problems but couldn't find any. Is it a problem specific to my computer and is there a fix?

---

### Post by 2F4U on 2011-12-24
Sounds to me like a problem specific to your hardware. Can you give more details about that hardware?

---

### Post by aepokh on 2011-12-24
Intel core i5-460M processor with 4GB DDR2 RAM. Hard drive is 640GB. Not sure of other specs; ASUS's webpage doesn't seem to have information and I've misplaced the documents from when I purchased the computer.

---

### Post by QIII on 2011-12-24
What do you have installed right at this moment?  Still both?  

Could you run the following in the terminal and post back the results

```
sudo fdisk -lu
```That is an "ell" not a "one".

fdisk is a utility for finding out a number of things about the fixed drives.  But it is possible for someone to give you bad commands, so be careful.  Cut and paste the code to be sure you get it right.

What this command will do is list the partition table with file system type and show some size information.

For more information, type

```
man fdisk
``` in the terminal

---

### Post by Nasair on 2011-12-24
Have you tried booting in the Ubuntu live thingy (technical term) and formatted the drive (not partition) to be a MBR with the disc utility? Or if not, what type is it?

Also, you said 640 GB...what kind of drive is this? Specific as possible please.

---

### Post by aepokh on 2011-12-25
> **QIII said:**
> What do you have installed right at this moment?  Still both?  

Could you run the following in the terminal and post back the results

```
sudo fdisk -lu
```That is an "ell" not a "one".

fdisk is a utility for finding out a number of things about the fixed drives.  But it is possible for someone to give you bad commands, so be careful.  Cut and paste the code to be sure you get it right.

What this command will do is list the partition table with file system type and show some size information.

For more information, type

```
man fdisk
``` in the terminal

If I had both installed, I wouldn't have made a thread asking how to achieve that, would I? Currently I have Windows installed on the hard drive and am running Ubuntu from a live disc. Regardless, the output of fdisk:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0299fa60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   209717247   104755200    7  HPFS/NTFS/exFAT

```GPT is the same thing that Windows was complaining about. What's strange is that I used GParted to create the partition table! I've tried many times to make something with GParted that can accommodate Windows, but Windows (and Linux too, apparently) has always reported that the partition table is GPT and thus Windows could not be installed.

> **Nasair said:**
> Have you tried booting in the Ubuntu live thingy (technical term) and formatted the drive (not partition) to be a MBR with the disc utility? Or if not, what type is it?

Also, you said 640 GB...what kind of drive is this? Specific as possible please.

Magnetic disc, 5200 rpm. I'm afraid that I can't be any more specific because Asus does not provide the full specifications to their products in a manner easily accessible from their website.

As for reformatting the disc, what sort of utility would I use? Everything on Google points to fdisk, but I can't find a way to actually format a disc using that. The closest I could do is try to rewrite the partition table, but that didn't seem to actually do anything:

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Command (m for help): o
Building a new DOS disklabel with disk identifier 0x7a97c9cd.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
[ ... same as before ]

```

---

### Post by QIII on 2011-12-25
I'm still not entirely clear on what you have tried, so bear with me.

When I used to dual boot on a single disk, I basically did this:  Installed Windows, used the Windows utilities to defrag; used the Windows utilities to shrink the Windows partition; installed Ubuntu side-by-side on the newly freed portion of the disk.
 
This might be helpful:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

 Is your installation of Windows currently stable?
 
 Can you use the tools in Windows to defrag (two or three times) and then  shrink the windows partition down (using the utilities in Windows itself) to where you have enough left for  your Ubuntu installation?  It is best to use the tools in Windows itself.

If you try that, how much room will Windows give up?
 
 Once you get some room, can you use gparted from the Live CD to make sure that the remainder of the disk is unallocated?
 
 Can you install Ubuntu and select the option to install side by side?  Note that you may not "see" the Windows partition from here, but just check to be sure that the size of the disk you are offered matches what you know was freed up by resizing the Windows partition.

---

### Post by Nasair on 2011-12-26
> As for reformatting the disc, what sort of utility would I use?

Just the disk utility in Ubuntu

If you're using the new Unity just search for disk utility.
A guide for Ubuntu 10.04 but same instructions:
[http://www.ubuntubuzz.com/2010/06/ubuntu-1004-disk-utility-tools_28.html](http://www.ubuntubuzz.com/2010/06/ubuntu-1004-disk-utility-tools_28.html)

Otherwise any luck since the last post?

---

### Post by aepokh on 2011-12-27
Solved.

Eventually I just dban'd the whole drive overnight, then used GParted to create a new partition table. That's probably what I should have done in the first place, and in retrospect I don't think I even needed the dban. (Though I wonder why fdisk didn't actually build a DOS partition table when it said it would.)

After that everything installs just fine.

---

### Post by Nasair on 2011-12-27
Just for my benifet, what is "dban'd"?

---

### Post by jim_deadlock on 2011-12-27
[Darik's Boot And Nuke]("http://www.dban.org")

---

### Post by jagibbs on 2013-01-12
aepokh, I don't think you realize the impact of what you've done.  There are many many people on the forums today (January 2013) still trying to get a dual boot of Windows and Ubuntu installed on their EFI machines which utilize GPT partitioning.

I've been at it for over a week on my new Macbook Pro reading forums and generally going insane.

You say you solved your problem by simply creating a partition table, but really don't say what that partition table was.  This could be the solution to my (and many others problem).

FYI, I believe the reason that the Ubuntu installer was not seeing your Windows installation or partitions when you tried to install Windows first, is because of a still-present (as of Jan 2013) bug in the libparted library that the Ubuntu installer uses.  Effectively, the size of the protective MBR that the Windows installation created in order to support GPT partitioning is confusing the Ubuntu installer.  Perhaps when you created your new partition table you accidentally? got something right.  I may be talking out of my 'donkey' also since I'm no expert.  I'm just speculating based on things I've read elsewhere.

If you can provide any detail on how you partitioned, what utility you used, and then which OS you installed first after the partitioning, that would be great!

---

### Post by jim_deadlock on 2013-01-12
This thread is over a year old, you should probably create a new one.

---

