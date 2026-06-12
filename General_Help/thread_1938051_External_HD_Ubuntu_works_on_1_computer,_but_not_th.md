---
title: "External HD Ubuntu works on 1 computer, but not the other"
date: 2012-03-09
forum: General Help
---

### Post by Utah1981 on 2012-03-09
Hello, 

I am somewhat new to Ubuntu, I have searched the forums for my issue but there are a lot of posts about external hard drives. If this problem is listed I didn't see it. 

I have a desktop computer(from Dell) that runs on windows 7. I also have a(HP) Laptop that dual boots windows 7 and Ubuntu 11.10(the dual boot is actually an accidental install). and i have a Western Digital 1tb external hard drive with 3 equal(well close to equal of about 300gb each) partitions. 1 of the partitions is NTFS for my windows file backups(Precautions have been taken in case this goes wrong). another partition has Ubuntu 11.10 in it. and the third partition is empty at the moment.

my issue is this: When the external hard drive is attached to my desktop, I can restart the computer so the external hard drive takes over and it will boot into Ubuntu, there is a purple boot loading screen that lets me choose which operating system to use. Everything seems to work fine there. However, when I attach the hard drive to my laptop and restart it like I do for the desktop(the external drive wont take over when the computer first turns on, only on restarts) I get a black screen with.  
 

 error: hd0 out of disk
 grub rescue>_
 

 I have ran a grub-update in the laptops Ubuntu with the external HD attached, the loading screen changed adding the external HD Ubuntu to the list. When i select the External hard drives Ubuntu i get an error Shown in the attached picture

---

### Post by Grenage on 2012-03-09
Is it possible that the drive it can't find (first line in the error) is present on the Desktop, thus cannot be found on the laptop?

Can you post the output of this while the External Ubuntu OS is loaded on the Laptop:

```
cat /etc/fstab
```

---

### Post by Utah1981 on 2012-03-10
I can't get the external drive to load Ubuntu while it its attached to the laptop. Closest I can get there is a grub rescue screen. I tried running this at the grub rescue prompt, it didn't work.

I then ran the command from the laptops internal Ubuntu while the external drive was attached. 

(user@computer):~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c2a9a134-ef6f-4488-b376-5ef0bb4e968d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e21bd3d1-7b67-4d51-bebb-0d42ed1add44 none            swap    sw              0       0
(user@computer):~$ 

This is what I get when I attach the external drive to the desktop

(user@computer):~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=de618330-dbaf-4936-baf9-ad23f26ac5e6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=033ec382-6bac-49ae-82ba-eb68d1d2dd89 none            swap    sw              0       0
(user@computer):~$

I'm pretty sure thats the external drive listed not sure why its being listed differently.

---

### Post by oldfred on 2012-03-10
While there used to be an issue with older computer where the BIOS would not boot from beyond 137GB, some newer computers seem to have a similar issue. It probably is a BIOS setting but laptops often do not have many BIOS settings.

You may want to compare two systems, but look at IDE vs LBA or ACHI.

Some other potential BIOS issues:

BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply

Quote from another thread.
> Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.


---

### Post by Grenage on 2012-03-12
I'd have to agree with oldfred here; the referenced partition is valid and local to the external drive, so it can't be a spread install.

---

### Post by Utah1981 on 2012-03-23
Changing the size for my Ubuntu partition to under 130 gig seemed to do the trick. The external drive works on both machines now. Thank you for the help.

---

