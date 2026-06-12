---
title: "External hard disk unable to be reformatted from ext4 to FAT or fat32"
date: 2011-08-19
forum: General Help
---

### Post by JamesParente on 2011-08-19
Hello, recently, I tried to install ubuntu 11.04 on my external hard drive (WD My Passport, thats all i remember about the name) and all was well, until I tried to reformat it from ext4 to FAT, and no such luck, it isn't even being READ, not in fdisk -l, not by gparted, disk manager, or anything else. Windows is no help at all... I tried that out of desparation. I am at a complete dead end, and any help would be appreciated, thanks!

---

### Post by Machiavelli on 2011-08-19
Try ext4 -> ext3 -> Fat32 or ext4 -> NTFS, good luck!

---

### Post by JamesParente on 2011-08-19
Thanks, but this is a new problem for me, can you go into more detail so I can learn for future references? For example, what program should I use to go from ext4 -> ext3 -> Fat32 or ext4 -> NTFS when I can't tell what the name of my external hard drive is? Thanks for your help

---

### Post by Machiavelli on 2011-08-19
try this one.

[http://www.webupd8.org/2011/02/rescue-lost-partitions-data-with.html](http://www.webupd8.org/2011/02/rescue-lost-partitions-data-with.html)

---

### Post by JamesParente on 2011-08-19
I tried GParted before, and no luck, GParted isn't even registering that my external is even there. Any other suggestions?

---

### Post by JC Cheloven on 2011-08-19
> **JamesParente said:**
> Hello, recently, I tried to install ubuntu 11.04 on my external hard drive (WD My Passport, thats all i remember about the name) and all was well, until I tried to reformat it from ext4 to FAT, and no such luck, it isn't even being READ, not in fdisk -l, not by gparted, disk manager, or anything else. Windows is no help at all... I tried that out of desparation. I am at a complete dead end, and any help would be appreciated, thanks!

If the disk is not even seen by gparted or palimpsest (aka gnome-disk-utility), most likely your disk is dead "due to natural reasons". That seldom occurs, but still it happens sometimes. Well, as desperate resort you could:

- Give us more details: USB disk? From where did you try to format to FAT, and why? (ie, what did you do exactly? what was you intent?) You have lost your ubuntu and you're running live sessions now? Post the output of your fdisk -l from live session.

- Check if it is seen when plugged to a different usb port, or a different pc. Perhaps it's a matter of the pc's USB bus, not the disk. If it's a usb-powered disk, try using a cable with an extra usb plug (used to aditional CC power). 

- Check from windows with some proprietary software (partition magic ...).

Good luck.
JC

---

### Post by JamesParente on 2011-08-19
Alright, well, I found that its a Western Digital My Passport Essential 500GB, I tried to format it in FAT on windows 7, because I was having trouble formatting it on ubuntu 10.10 (I wanted to upgrade to 11.04 and eventually 11.10, but on the usb external) 

fdisk -l for some reason isn't working as of now -_- however, remembering back to when it did work when I did it a couple hours ago, the port that my external was in was percieved as having nothing in it. 

I am reasonably sure it is the disk, and not the port, because other usbs I have work in the port, but I'll see if switching them around works. 

My external isn't even seen on windows any more, and I'm not sure what to do... I would rather put all my energy into trying to fix this problem before spending even more money! haha

Thanks for your help, I'll keep you posted if I find anything else.

---

### Post by 23dornot23d on 2011-08-19
Also if its a USB Drive ......

When the computer is powered off .....

Unplug the USB ........ if it has a power chord that plugs into the back unplug it too ....

( I have had a situation where the USB 1 terra does not pick up .... and have to use this
routine everytime on my older computer - to get it to recognise it ..... )

1 .... count to 10 then Plug the power cable back into the USB Drive .....
2 .... Now plug the USB cable back into the computer ......
3 .... Boot the computer up ....... hold down the F11 key ..... or whatever key allows 
you to boot from another drive ...... and first check that the BIOS sees the Drive ok.

If it does not then try the above again ..... if it fails to see it the next time then 
I would start looking to see if the drive is faulty ,,,,,

Possibly try it on another machine to see if it is recognised .......

Also be aware that the drive needs to have been unmounted properly if
it was used on a Windows computer .....

Other than that that's all I can say ..... :confused:

You need to use .....

sudo fdisk -l 

[COLOR=Red]**as fdisk -l ( shows nothing on mine either - yet there is one drive with 8 partitions on it and a SD card shoved in the front )**[/COLOR]
```

keith@keith-MS-7181:~$ fdisk -l

keith@keith-MS-7181:~$ sudo fdisk -l
[sudo] password for keith: 

Disk /dev/mmcblk0: 2059 MB, 2059403264 bytes
38 heads, 37 sectors/track, 2860 cylinders
Units = cylinders of 1406 * 512 = 719872 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        2861     2011104+   6  FAT16

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a32b4b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       27084   217552198+   c  W95 FAT32 (LBA)
/dev/sda2           27085       29545    19767982+  83  Linux
/dev/sda3           29546       35497    47802285+   f  W95 Ext'd (LBA)
/dev/sda4           35497       38913    27445248   83  Linux
/dev/sda5           29546       32050    20121349+  83  Linux
/dev/sda6           34775       34962     1510078+  82  Linux swap / Solaris
/dev/sda7   *       32051       34774    21880498+  83  Linux
/dev/sda8           34963       35496     4287488   83  Linux

Partition table entries are not in disk order
keith@keith-MS-7181:~$ 


```

---

### Post by JC Cheloven on 2011-08-20
> **JamesParente said:**
> Alright, well, I found that its a Western Digital My Passport Essential 500GB, I tried to format it in FAT on windows 7, because I was having trouble formatting it on ubuntu 10.10 (I wanted to upgrade to 11.04 and eventually 11.10, but on the usb external) 

fdisk -l for some reason isn't working as of now -_- however, remembering back to when it did work when I did it a couple hours ago, the port that my external was in was percieved as having nothing in it. 

I am reasonably sure it is the disk, and not the port, because other usbs I have work in the port, but I'll see if switching them around works. 

My external isn't even seen on windows any more, and I'm not sure what to do... I would rather put all my energy into trying to fix this problem before spending even more money! haha

Thanks for your help, I'll keep you posted if I find anything else.

HEY, you should do it as superuser: ```
sudo fdisk -l
```
Please post the output and let's start by the beginning.

---

### Post by Wim Sturkenboom on 2011-08-20
From the image shown in post #7, I agree with JC.

And what did you try in Windows? Disk management?

---

### Post by JamesParente on 2011-08-20
Here is my sudo fdisk -l screenshot, 

I currently have plugged in my external as well. I did use disk management in windows, and that didn't work either.

---

### Post by JamesParente on 2011-08-20
Additionally, I don't don't know if this is a problem, but at the same time my external stopped being registered by any computer, it is also making this odd beeping noise like it's trying to be read, and its obviously not being read.

---

### Post by Wim Sturkenboom on 2011-08-20
> **JamesParente said:**
> Additionally, I don't don't know if this is a problem, but at the same time my external stopped being registered by any computer, it is also making this odd beeping noise like it's trying to be read, and its obviously not being read.Sound like a dead drive.

And the new *fdisk -l* shows sda (I assume your internal HD) and a 256MB device; maybe an old usb memory stick :confused:

---

### Post by JamesParente on 2011-08-20
Yeah, at one point when I put Ubuntu on my external it said something about a GRUB issue, and its been terrible ever since... so by a "dead drive" you mean that I've got to buy a new disk? I only ask because it does power on, its just not read. However, if I've got to get a new usb external, I can do that.

---

### Post by JC Cheloven on 2011-08-20
Hi again James, some random ideas:

- First off, to post the outputs of commands at terminal, you don't need to take a screeshot; that's unnecesarily heavy and it overloads the forums. In the future, please select with the mouse the desired text in the terminal, then do edit->copy from the upper menu, go back to the post in the browser, and do edit->paste (or ctrl-V).

- Something in your output seems strange. You said you tried to reformat your external hard disk from within windows, so I'd expect windows to be installed in sda (most likely in sda1). But it isn't. You have only a linux partition and a swap partition there. :confused: 

- With the info you provided, I'd also say that it is a hardware issue with your external HD. But we can't know really, as the aforementioned information is quite contradictory, and we cannot figure out so far what you actually did (as mentioned in the previous paragraph).

- Unless someone else has a better idea on how to collect data for this issue, your possible course of action would be bringing the disk to a specialized store to get a hands-on opinion and eventually a solution. I'm afraid next step would be purchasing a new one.

Best
JC

---

### Post by JamesParente on 2011-08-21
Thank you so much for the tips, and the advice about the terminal stuff! I'll work on my situation, hopefully I can stop it from happening for someone else. Thanks again, everyone, for your help!

---

