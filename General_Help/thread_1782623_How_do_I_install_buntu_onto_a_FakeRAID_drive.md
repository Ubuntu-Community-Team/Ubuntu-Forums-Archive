---
title: "How do I install **buntu onto a FakeRAID drive?"
date: 2011-06-14
forum: General Help
---

### Post by chipppy on 2011-06-14
Good Morning

I am trying to install Mythbuntu onto a FakeRAID system.
I have setup my new MythTV box with FakeRAID (ICH10R chipset), using 5 X2TB HDD's

I have setup two partitions 
dm-0 = 500GB (OS)
dm-1 = 7TB (storage)

I have got that part working and I can format it to ext4 and I can seedm-0, and dm-1.  No problem here

I then try to install Mythbuntu and all goes well until it gets to installing the bootloader.
At this point it stops saything that it cannot install bootloader onto sda.
I am assuming that it needs to be installed onto dm-o.  I cannot figure out how to get the install process to install the bootloader onto dm-0 and finish installing.

The is an option to install bootloader manually later but I have no idea how to do that

Can anyone help me please

Cheers
chipppy

---

### Post by wolfen69 on 2011-06-14
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by psusi on 2011-06-14
Unless you need to dual boot with Windows, you should use Linux software raid instead of fakeraid, since it is much better supported.

---

### Post by chipppy on 2011-06-16
Good Morning

Using Mythbuntu 10.10

Used the manual partition section and all going well.

I had to use Gparted to format dm-0 to start with.  Then did install and all seemed to work once i put a mount point in (/), but would reboot.  Complained about timing out error and then drop to shell.

I thought I did something wrong during the install, so had another go.  Repeated steps without the GParted format and notice that the swap partition was on the harddrive.  Left the swap in place and installed over the existing installation.
this time all worked fine and has restarted a few times and all updates done.  did an upgrade to 11.04 and all looks good.  Mounted the second FakeRAID partition into installation and all working great.

appears that the mount and swap needs to be defined before doing the install to get things working correctly.

Thanks heaps for the help.

As to using FakeRAId v LinuxRAID.  I cannot understand how to do linuxRAID.  The FakeRAID was easy to follow in the manual and appears to have worked fine.
I feel someone needs to write up a step by step how to create LinuxRAID.  Much more detailed then the guide linked to by wolfen69, for use non-gurus.  I am an intermediate used of linux (I think) but i still need the detailed step by step and the basic users need them aswell.
anyone want to try and write one.  I have my system work and the wife will kill me if she misses another TV show so i not going to risk rebuilding myth box again sorry.

Cheers
chipppy

---

### Post by psusi on 2011-06-17
The fakeraid currently won't handle arrays > 2 TB.

---

### Post by chipppy on 2011-06-18
Good Evening

Yep ICH10R chipset can only do a bootable partition of <2TB but can handle larger not-bootable partitions.  Dont ask Gigabyte about it though as they dont seem to know this simple fact, that a websearch finds reasonably quickly.

In terms of the installation all is working fine.  The OS is installe don dm-0 and it boot without any issues

Cheers
chipppy

---

### Post by psusi on 2011-06-19
It has nothing to do with the chipset; dmraid simply does not understand GPT.

---

### Post by chipppy on 2011-06-19
Good Morning

You might be able to help with my auto mounting of the 7TB partition problem.

I have the OS working great but I cannot get the 7TB part to automount on a reboot.  It is mountable via sudo mount -a

I have more detail in thread [http://ubuntuforums.org/showthread.php?t=1785888]("http://ubuntuforums.org/showthread.php?t=1785888")

Cheers 
Chiiipy

---

