---
title: "mount"
date: 2010-12-16
forum: General Help
---

### Post by jim allAn on 2010-12-16
[FONT=-moz-fixed]   I need a file system type to get further with this command. 
"sudo mount /dev/sdc /home/jim/desktop/flash" 
   Which file system would I put there and what would be the corrected  command.  I have been experimenting with it but getting nowhere. 
[LEFT]   The dev sdc is my flash drive and home jim desktop flash is where I  think it goes into the flash folder. 
[/LEFT]
[/FONT]

---

### Post by MooPi on 2010-12-16
So you want you flash drive to mount to the desktop folder ? If that is the case you'll need to edit what is called the /etc/fstab file.
Can you give us the results of terminal commands ```
sudo fdisk -l
```
And ```
sudo blkid
```
This will give us the location and ID of the drive in question.

---

### Post by jim allAn on 2010-12-16
> **MooPi said:**
> So you want you flash drive to mount to the desktop folder ? If that is the case you'll need to edit what is called the /etc/fstab file.
Can you give us the results of terminal commands ```
sudo fdisk -l
```
And ```
sudo blkid
```
This will give us the location and ID of the drive in question.
jim@jim-desktop:~$ sudo fdisk -l
[sudo] password for jim: 
Sorry, try again.
[sudo] password for jim: 

Disk /dev/sda: 10.2 GB, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046f87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1182     9488384   83  Linux
/dev/sda2            1182        1241      472065    5  Extended
/dev/sda5            1182        1241      472064   82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcaf7caf7

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 2000 MB, 2000682496 bytes
62 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
jim@jim-desktop:~$ 


jim@jim-desktop:~$ sudo blkid
/dev/sda1: UUID="0bddd55a-bc7d-4783-a504-a1d2ca26bfc7" TYPE="ext4" 
/dev/sda5: UUID="0732ccce-0d20-4a17-a197-82adb0966e8b" TYPE="swap" 
jim@jim-desktop:~$ 
   I don't even see my sdc here but maybe you were looking for a file type.

---

### Post by dabl on 2010-12-16
There's no /dev/sdc connected to that system!

USB flash drives should not require manual mounting, anyway.

Is it a good USB stick -- do other (Windows) computers see it?  Is there anything special going on there -- have you reformatted it, or modified your Ubuntu system in some way?  Is there a KVM switch or other external connector involved in this?

Try (with the flash drive NOT connected) rebooting your Ubuntu system.  After you've logged in, then just insert the flash drive into the USB connector.  What do you see -- does the notifier pop up?  What output do you get from ```
lsusb
``` in the terminal?

---

### Post by jim allAn on 2010-12-16
The system says there is in more than one place.  I have three programs that claim there is.
> **dabl said:**
> There's no /dev/sdc connected to that system!

USB flash drives should not require manual mounting, anyway.
Maybe it shouldn't but it is.  Maybe I got some kind of outlaw.
Is it a good USB stick -- do other (Windows) computers see it?  Is there anything special going on there -- have you reformatted it, or modified your Ubuntu system in some way?  Is there a KVM switch or other external connector involved in this?
  It is working in widows all right.

Try (with the flash drive NOT connected) rebooting your Ubuntu system.  After you've logged in, then just insert the flash drive into the USB connector.  What do you see -- does the notifier pop up?  What output do you get from ```
lsusb
``` in the terminal?
    I will send this out so I don't lose.  Then try the reboot thing and let you know the results.

jim@jim-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0781:5530 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:080f Logitech, Inc. 
Bus 001 Device 002: ID 067b:25a1 Prolific Technology, Inc. PL25A1 Host-Host Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jim@jim-desktop:~$   
   Well I didn't lose it after all.
   I did the reboot and plugged in the drive but I saw no notifier such as widows says new hardware found.
  This thing is just a witch.

---

### Post by dabl on 2010-12-16
Is it the Sandisk?  So, the USB bus sees it, but the kernel does not recognize it as a block device, i.e. it doesn't look like a hard drive.  Does it have that Sandisk faux CD-mounter software on it?

I like the Sandisk Cruzers, but I normally use "dd" to nuke the partition table, and then use GParted to partition/format it.  Also, there's an old HP MS-DOS/Windows executable that will reset a USB stick to un-partitioned status -- the copy I have is named "cp006049.exe" -- you should be able to Google it and download it.

---

### Post by jim allAn on 2010-12-16
> **dabl said:**
> Is it the Sandisk?  So, the USB bus sees it, but the kernel does not recognize it as a block device, i.e. it doesn't look like a hard drive.  Does it have that Sandisk faux CD-mounter software on it?

I like the Sandisk Cruzers, but I normally use "dd" to nuke the partition table, and then use GParted to partition/format it.  Also, there's an old HP MS-DOS/Windows executable that will reset a USB stick to un-partitioned status -- the copy I have is named "cp006049.exe" -- you should be able to Google it and download it.

   It is the sandisk.  I don't know really because I can't check.
   So far the system says no partitition or anything.
   Except for the fact I no longer have windows on this puter but I do have on the other one.  I could switch it over but I think in this case we wouldn't gain anything.  Wait why couldn't I dld it on the windows box, temporarlly put the sandisk on the windows box and get it to an unpartitioned state then put it back on Ubuntu.  That's what I will try tomorrow morning.
   Meanwhile there must be a cmd using fdisk that would tell for sure if it is partitioned.  I might put a partition on it in the future so I could put some windows stuff on it.  That's for after I learn how to manage it a little better.

---

### Post by dabl on 2010-12-17
> **jim allAn said:**
> 
   Meanwhile there must be a cmd using fdisk that would tell for sure if it is partitioned. 

fdisk only works on block devices that are recognized by the kernel.  Your device is not being recognized as a drive.  Yes, if it were recognized, then ```
sudo fdisk -lu
``` would show the partitions and their beginning and ending sectors.

The Sandisk software that I was thinking of is called "U3".  It makes the thumb drive present itself to Windows as a CD.  I've seen different effects in Linux -- sometimes it looks like a CD and sometimes like a tiny hard drive.  It is not helpful, that's why I use "dd" or the HP utility to nuke it, before I repartition the thumb drive for Linux use.

---

### Post by jim allAn on 2010-12-17
> **dabl said:**
> fdisk only works on block devices that are recognized by the kernel.  Your device is not being recognized as a drive.  Yes, if it were recognized, then ```
sudo fdisk -lu
``` would show the partitions and their beginning and ending sectors.

The Sandisk software that I was thinking of is called "U3".  It makes the thumb drive present itself to Windows as a CD.  I've seen different effects in Linux -- sometimes it looks like a CD and sometimes like a tiny hard drive.  It is not helpful, that's why I use "dd" or the HP utility to nuke it, before I repartition the thumb drive for Linux use.
Disk /dev/sdc doesn't contain a valid partition table

   I hadn't remembered it last knight, but I can't check for a partition on sdc on my windows box because it only has two usb ports and they are in use for the keyboard and mouse.  Switching is a pain ]sudo fdisk -lu[with my eyes and the lighting in the room.
   However, I ran the fdisk sudo fdisk -lu anyway and it did mention that there was no valid partition on the sdc drive.  The output was "Disk /dev/sdc doesn't contain a valid partition table."
   So where are we now?

---

### Post by dabl on 2010-12-17
> **jim allAn said:**
> 
 The output was "Disk /dev/sdc doesn't contain a valid partition table."


OK, well, that's useful information.  Do you have GParted available, either from a running system or a live CD?  Personally I like the Parted Magic Live CD for these adventures, but as long as you can run GParted it probably doesn't matter.

BE CAREFUL AND BE SURE YOU ARE LOOKING AT THE USB STICK AND NOT A REAL HARD DRIVE WHILE YOU DO THE FOLLOWING!

You'll need to browse to the device /dev/sdc, then on the graphic right-click and make sure it is unmounted (Parted Magic makes this part easier).  Then up on the top menu you will choose "Device > New Partition Table", and choose "MS-DOS" for the table type.  As soon as you "Apply" or "OK" or whatever, you'll probably see your device notifier pop up with an announcement that it found a drive.  Just ignore that.  If it auto-mounts it, use GParted again to unmount it -- it needs to stay unmounted for the moment.

Back in GParted, right-click the unallocated space on that device, and format it to FAT32 (assuming you just want it for a single-partition storage device). Click "Apply" and be done.

That's it. You can remove the device, and when you re-insert it, it should be recognized and mounted automatically under /media.

Always use "safely remove" or "eject" (as applicable)in your file manager, whether Linux or Windows, to eject a flash drive.  FAT32 is not a very rugged filesystem and won't take very many instances of just being yanked out before you've got troubles again.

---

### Post by jim allAn on 2010-12-17
I hope you got the private mess.  The other one was to short, or so it said.  Then that gave me problems as it included the whole mess as your name.  Naturally that wouldn't work but I think i found a way around that.  Anyway the second tine I submitted it there were no errors so I think it went out to you.

---

