---
title: "How to uninstall ubuntu netbook."
date: 2010-11-29
forum: General Help
---

### Post by SenorEpic on 2010-11-29
Hi, so I am pretty new to everything related to linux and I currently have ubuntu netbook remix installed as the only OS on my netbook. I've been looking everywhere but I can't find any place where there is a method to remove ubuntu and reinstall windows 7.
Can anyone help me?

---

### Post by Hawkoon on 2010-11-29
So you had Windows 7 installed before you installed Ubuntu? How did you setup Ubuntu, did you create a separate partition for it, did you install it in the same partition as Windows or did you just format your drive during the Ubuntu installation?

If you show us the output of ```
fdisk -l
``` that would help. Run this command from a terminal session. You will have to run it with root (administrator) permission, you do this by sticking sudo in front of the command, so ```
sudo fdisk -l
```

---

### Post by SenorEpic on 2010-11-29
Yes, I had windows 7 before installing ubuntu, and I think I may have removed the anything windows related in the process... :S
This is what I got after typing in that command:

fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

---

### Post by mikewhatever on 2010-11-29
Removing Ubuntu is really simple, just delete its partitions and you are done. You can do it with Gparted from the live USB.

---

### Post by SenorEpic on 2010-11-29
if I do that, how do I reinstall windows without a disk drive?

---

### Post by holycow131415 on 2010-11-30
You will need to find a computer where you can install unetbootin so that you can create a bootable usb stick from your windows 7 disc to put into your netbook.

This is why netbooks should not be primary computers. =)

[http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/](http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/)

---

### Post by Hawkoon on 2010-11-30
> fdisk: invalid option -- '1'

You used number "1" as command switch, it should have been the letter "l". If you get an error message back from a command about wrong parameters etc..., you can get help on how to use the command properly by typing "man" (for manual) followed by the command.

If you wiped your entire drive it doesn't matter anyway. I thought there might be a chance Windows is still sitting somewhere on your drive and you just cannot boot it up right now.

---

### Post by rummy77 on 2010-11-30
If you're going to install windows fresh, you might be best trying to use a windows restore disk on a flash drive (hopefully you made one before deleting windows).  If you don't have a restore disk, you could try an external DVD drive and a windows install disk.  Windows should be able to format your HD when it installs.

---

### Post by Hawkoon on 2010-11-30
If you follow through with holycow131415's instructions you should be sorted.

Alternatively, maybe you can get hold of a DVD drive? Your netbook should be able to boot from it. I use a standard desktop DVD drive via IDE 2 USB adapter. Works like a charm.

---

### Post by Hawkoon on 2010-11-30
[]("http://ubuntuforums.org/member.php?u=1183784")rummy77, you beat me to it by 2 minutes :)

---

