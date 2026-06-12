---
title: "Bootable USB"
date: 2011-11-25
forum: General Help
---

### Post by ExpL0it0R on 2011-11-25
Hi everybody. I've been working on creating a bootable USB device for the whole day. But it seems that i can only find windows files to do the job automatically and i've been trying to use them via wine, which seems not to work properly as it can't reach the USB device and else... Can someone tell me how i can create a bootable USB so that when i copied my files in it, i can run directly ? I want to make a setup USB not a live one btw. Thanks.

---

### Post by BC59 on 2011-11-25
I don't know if I understand what you like to do.

If you like to create your custom operating system, means to install an OS in your USB and use it to boot, work through USB (Live CD style) or even install this OS, there is Remastersys.

You install Ubuntu on a computer, you remove or add the apps you like, wine etc and then you backup everything in an .iso file. When you burn this image you have your own working system in a USB.

---

### Post by ExpL0it0R on 2011-11-25
I want to make a USB so that i can install an operating system without using a DVD/CD. For instance, i have a Win7 DVD, and i want to install the files via USB, not the DVD.

---

### Post by BC59 on 2011-11-25
To make a bootable USB with Windows you need a program like UNetbootin.

For Ubuntu you can use Startup Disk Creator.

More or less they are installing the OS image to a USB and create a Live CD.

The only difference is that in Windows it's impossible to work the system through the USB, only you can install it.

---

### Post by ExpL0it0R on 2011-11-25
Thank you. But i couldn't manage to do that with startup disk creator. However i downloaded unetbootin for linux but it doesnt detect my USB drive.

---

### Post by ExpL0it0R on 2011-11-25
I think the reason unetbootin doesnt detect the drive is that the Startup Disk Creator couldnt clearly erase the disk and format it because it gave an error when i tried to erase disk;


```
org.freedesktop.UDisks.Error.Failed: Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdb, start=0, size=990904320, type=0x0c
Entering MS-DOS parser (offset=0, size=990904320)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed

```

Thanks in advance.

---

### Post by roger_1960 on 2011-11-25
Hi

Not quite sure what you are trying to do.

Download and install Unetbootin onto your PC running Ubuntu.

Download and save the .iso file onto your PC.  (The .iso which you are going to use to create a bootable/installable USB drive.)

Run unetbootin.  Select the iso file and the USB drive (be sure to get the drive selection correct).  Run unetbootin.

In your post #6 I dont understand the bit about the startup disk erasing the disk?

---

### Post by ExpL0it0R on 2011-11-25
I ran Startup Disk Creator in which existed in administrator tools of Ubuntu. When i click on 'Erase Disk' button, i get that error and now it seems i can't reach my USB device.

CRUCIAL edit:

Now i am seeing a new function of UNetbootin after installing it which is Show All Drives. As far as i know my USB device is /dev/sdb which can be seen when the function is selected. But i still can't reach my USB device directly.

---

### Post by roger_1960 on 2011-11-25
If you connect the USB device (is it a Hdisk drive or a USB stick?) is it detected in Nautilus file manager?  If so, right click and unmount it then format it.  I would then try using Unetbootin.

---

### Post by ExpL0it0R on 2011-11-25
No i can not reach it via the file manager and that is the main problem actually and its a USB stick.

Edit:

I can see the device in Ubuntu's Disk Utility Tool. Should i create a partition in order to reach it via the file manager ? / I guess so ? :]

---

### Post by efflandt on 2011-11-25
Install Gparted if not already installed.  See what it shows for the USB drive.

With Startup Disk Creator it is very easy to accidentally format the "drive" (sdb) instead of the "partition" (sdb1), at which point there is no longer a partition table, much less any partition to format.  I did that repeatedly for awhile.

You could use Gparted to create a new ms-dos partition table and then a partition.

---

### Post by Paddy Landau on 2011-11-25
Plug in your USB.
Run either GParted or Disk Utility (whichever you feel more comfortable with).
You will be able to delete the existing partition, recreate it, then format it -- I recommend FAT32. You will lose all data on the USB.
Beware... If you accidentally choose the wrong drive, you could lose your data, operating system or both. Therefore, be very sure you have chosen the right device at _every_ stage of the operation.

---

### Post by roger_1960 on 2011-11-25
Can you "see" the USB stick in any other PC, it could be faulty.

---

### Post by ExpL0it0R on 2011-11-25
I get the same error when trying to create a partition in Disk Utility.
```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdb, start=0, size=990904320, type=0x0c
Entering MS-DOS parser (offset=0, size=990904320)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed

```

Edit:

And as in Disk Utility, /dev/sdb seems to have an unallocated file system in GParted.


> **roger_1960 said:**
> Can you "see" the USB stick in any other PC, it could be faulty.

I was able to reach the USB stick before that process a couple of hours ago but i didn't try it on another PC afterwards.


> **Paddy Landau said:**
> Plug in your USB.
Run either GParted or Disk Utility (whichever you feel more comfortable with).
You will be able to delete the existing partition, recreate it, then format it -- I recommend FAT32. You will lose all data on the USB.
Beware... If you accidentally choose the wrong drive, you could lose your data, operating system or both. Therefore, be very sure you have chosen the right device at _every_ stage of the operation.

I did this and although it formatted it into FAT32 and Ubuntu said the device was found, there is a message 'Unable to Mount Filesystem'

---

### Post by ExpL0it0R on 2011-11-25
Urgh... Any help over there ? I've found a thread on the forum but i don't know how to do that troubleshooting stuff.

[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)

---

### Post by Paddy Landau on 2011-11-26
> **ExpL0it0R said:**
> I did this and although it formatted it into FAT32 and Ubuntu said the device was found, there is a message 'Unable to Mount Filesystem'
When specifically do you get this error: when rebooting, when trying to mount under Linux, ...?

---

