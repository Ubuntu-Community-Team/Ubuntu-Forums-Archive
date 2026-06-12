---
title: "Dual boot windows 7 and Ubuntu 10.10"
date: 2011-01-28
forum: General Help
---

### Post by Master Ninja on 2011-01-28
I am having problems with dual boot, I've read a number of tutorials but they're just confusing. I'll try to list my information to make things easier:

My hard drive (500GB) has:

System (200Mb)
Drive C (450Gb)
Drive D - Recovery (16GB)
HP Tools (100Mb)

I've shrunk drive C to 400Gb in Windows, thus creating 50Gb of unallocated space. I'm not interested in creating a swap partition at this time, all I want is to get Ubuntu on the 50Gb partition.

When I boot the Ubuntu CD, what do I have to do from this step?
If I go to select the partition manually, I can't use the 50Gb.

---

### Post by mharrison on 2011-01-28
> **Master Ninja said:**
> I've shrunk drive C to 400Gb in Windows, thus creating 50Gb of unallocated space. I'm not interested in creating a swap partition at this time, all I want is to get Ubuntu on the 50Gb partition.

I'm curious is the Windows partition is a logical partition and resizing it only allows you to create a new logical partition from within Windows.

What does the partition table look like when you are using the Manual Partition option from the Ubuntu CD?

---

### Post by Master Ninja on 2011-01-28
Sorry for the long reply, I had to boot the live CD.
I have no idea what's a logical partition but here's what it looks like from Gparted:


[http://img38.imageshack.us/img38/6038/screenshotvak.png](http://img38.imageshack.us/img38/6038/screenshotvak.png)

---

### Post by mharrison on 2011-01-28
> **Master Ninja said:**
> Sorry for the long reply, I had to boot the live CD.
I have no idea what's a logical partition but here's what it looks like from Gparted:


[http://img38.imageshack.us/img38/6038/screenshotvak.png](http://img38.imageshack.us/img38/6038/screenshotvak.png)

Ok, hopefully someone else comes along on this or I will have to take a look at the screenshot after I get out of work.  Apparently my employer has imageshack blocked.  Sorry :(

---

### Post by abdulapopoola on 2011-01-28
You don't need all the trouble.
At step 4 of the installation process, select install Ubuntu side by side with Windows - though there is a bug with this in Ubuntu 10.10.
Since you already have 50GB, just select install to largest contiguous space.
Have fun.

---

### Post by Master Ninja on 2011-01-28
I attached the image, have a look if you wish

---

### Post by Master Ninja on 2011-01-28
abdulapopoola, how can I do that, I've never seen that option, which option do I have to pick to get to that option, "select partitions manually" or the regular installation?

---

### Post by bryanl on 2011-01-28
You can have only 4 primary partitions in an MBR type disk schema and it appears you have that. This is most likely why you cannot create another partition. 

That 'system' partition is a system for what? 

In order to create another partition, you'll need to rearrange things so that one of your existing primary partitions becomes a sub partition in an extended partition. Then you can put an ubuntu in that extended partition, too. gparted on the Ubuntu Live CD works well to do the partition rearranging. Always make sure you can boot windows after partition fixing before installing Ubuntu as its partner on disk.

The 'hp tools' partition probably has the Windows BootMgr files on it. You can probably copy these files to your Windows 7 system partition and do away with it. You do need the BootMgr file in order to boot Windows 7.

You should also make the system restore DVD's for Windows 7. There should be a utility in the menu for this. That will create a bootable DVD set to replace the 'Recovery' partition function. You might need this if you mess things up like I do!!

Once you get the partitions straight, you can install Ubuntu and it will replace the disk MBR boot code with GRUB2 bootstrap code. That will refer to the /boot partition on the Ubuntu installed partition for the remainder of its files and it should detect the Windows 7 system so it will show up in your boot menu.

See [Drive upgrade: Ubuntu and Windows 7 dual boot main drive](http://tcl.leipper.org/2011/01/drive-upgrade-ubuntu-and-windows-7-dual-boot-main-drive/) and [Move to swapfile rather than swap partition](http://tcl.leipper.org/2009/08/move-to-swapfile-rather-than-swap-partition-2/) for additional ideas.

Also don't forget WUBI or whatever it is that will install Ubuntu inside windows. That would get around the partition problem

---

### Post by teh603 on 2011-01-28
The way I've always set this up is to completely format the drive, and then install Win7 from your system recovery on the freshly-erased disc. Poof, bang, "fresh" drive. Do this because an OEM install of Win7 has a way of maxing out the partitions on a drive, probably to make dual-booting or multibooting hard.

Once you have Win7 up and running properly, put your (K)Ubuntu CD into the drive, restart, and then reboot from the CD/DVD/whatever. When you get to the partitioning screen, the default option from the installer will give you the option to set up multibooting. The partitioner will shrink the Win7 partition, create two more in the freed-up space (one for Ubuntu and one for swap), and then do the install.

Your next reboot into Win7 will take a while as it does some kind of checksum on the disc to make sure everything's intact. Just take a coffee break and let your computer percolate.

Once its done, you'll now be able to use the GRUB menu to choose between Win7 or Ubuntu on boot, although Ubuntu will be the first menu item and thus the default.

---

### Post by Master Ninja on 2011-01-28
@teh603: I'm actually did a fresh recovery, thanks

@bryanl: I don't know what's the system partition, but I will take your advice, I can probably even get rid of the recovery partition as it's just to boot and recover, thanks

---

