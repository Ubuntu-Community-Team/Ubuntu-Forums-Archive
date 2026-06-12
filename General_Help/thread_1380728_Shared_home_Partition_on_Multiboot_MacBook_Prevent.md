---
title: "Shared /home Partition on Multiboot MacBook Prevents Login"
date: 2010-01-14
forum: General Help
---

### Post by bkadoctaj on 2010-01-14
Hey everyone,

I'm sorry to ask for help on this issue, but I've spent the entire day trying to get this to work.  I have a MacBook 4,1 which had the following set up this morning:

Partition with Mac OS X Snow Leopard
Partition with Ubuntu 9.10 Karmic Koala 64-bit
Partition with Windows 7 Ultimate 64-bit

I decided after some research that I would like to share the home directory between Mac OS X and Ubuntu (main user in both).  Initially I used Gparted Live to shrink my very large Mac OS X partition (after disabling journaling).  Then I created a new HFS+ primary partition in the free space.  This partition is sda5.  Partitions sda1, sda2, sda3, and sda4 are all used as well.

Following this, I used the Mac OS X Terminal in conjunction with the root user to move my Users directory onto sda5.  That being successful, I deleted the original Users directory on the Mac OS X boot partition.  Then, still in root, I modified the main user (jason)'s home directory in Advanced Settings to "Volumes/DATA/Users/jason" (where DATA is the LABEL of sda5).

Now, I reinstalled Ubuntu over the old installation (without a swap partition... simply a / mount point).

Then I followed all the necessary steps here to change my UID/GUID to 501:
[http://ubuntuforums.org/showthread.php?t=486483](http://ubuntuforums.org/showthread.php?t=486483)

Nonetheless, every time I've tried to boot into Ubuntu, I've obtained the following error before I even have the option to log in as jason:

> One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for /dev/sda5/Users
Press ESC to enter a recovery shell

Here is the text regarding the /home mount point in /etc/fstab:

> /dev/sda5/Users /home hfsplus defaults 0 2

Note that I have also tried "/dev/sda5" where I currently have "/dev/sda5/Users"; I had no success that way either.

Now, what I think the main issue is is that "sudo fdisk -l" returns:

> /dev/sda1   ........... ee GPT
/dev/sda2    ........... af HFS / HFS+
/dev/sda3 *  ........... 83 Linux
/dev/sda4     ..........   7 HPFS/NTFS

^ No mention of sda5 whatsoever...

I'm uncertain what to do at this point...  Any advice would be greatly appreciated.  Thanks for reading, everyone.  :)

---

