---
title: "How do I format a USB flashdisk or external hard drive?"
date: 2010-07-28
forum: General Help
---

### Post by berniedd on 2010-07-28
I'm quite new to this, and am running Ubuntu 9.04 version. My wife's USB flashdisk has picked up viruses from computers running Windows in her office. My quick solution is to format it (and external hard disks as well) in my machine. Please advise on how I do this?

---

### Post by TeoBigusGeekus on 2010-07-28
Open gparted (gnome partition editor), unmount the volume and format it as fat32.

---

### Post by aeiah on 2010-07-28
use gparted. if installed, it'll be in system > administration > gparted

if not installed, install it with software center, synaptic or with the command ```

sudo apt-get install gparted
```

you cant format or edit partitions on mounted devices, so you'll have to make sure the usb stick is unmounted if it automatically mounts when you plug it in.

---

### Post by sXeChris on 2010-07-28
This may be a bit irrelevant but upgrade to 10.04! It's very worth it.

---

### Post by martine4161 on 2010-07-28
It is very interesting post. it is very easy to Format your USB or external hard drive. USB (Universal Serial Bus) flash drives are rewritable storage devices designed to be portable and easy to use. Plug your flash drive into an empty USB port []("http://www.ehow.com/how_4963426_format-usb-flash-drive-ubuntu.html#")then back up any data on the drive.Enter your Ubuntu administrator password when prompted. Go to the Ubuntu main menu after the installation is complete. Click on "GParted" in the toolbar. Right-click on the device again (after it is unmounted) and then hover over "Format to.Close GParted after the flash drive is formatted.[LEFT][COLOR=#000000]

[/COLOR][/LEFT]

---

### Post by berniedd on 2010-07-28
Thanks for the quick response, guys. It has certainly worked for me. A few clarification points, though. Aeiah, I had to use Terminal to get Gparted installed. It then showed up in the System --> Administration --> Partition Editor. Since any USB device is automatically mounted by the computer as soon as I insert it into the USB socket, I had to unmount it. This I did by right clicking on its icon on the desktop. Returning to the Partition Editor window that opened up earlier, I had to select the device I wanted (the USB flashdisk), since the default choice that showed was the hard drive and its partitions. But the choices for the Partition drop down menu were all greyed out,hence not useable. I finally figured I had to use the refresh button, after which the choices for the Partition drop down menu now showed up, including the different File Allocation Table systems. Strangely, they did not include the HFS+ used by Apple nor the NTFS used by Microsoft. I thought this might be because Ubuntu does not natively read these two latter systems? Anyways, FAT32 was available, which is the choice I wanted.

Thanks again for the help, all.

---

### Post by TeoBigusGeekus on 2010-07-28
Next time don't be too quick to format the flash drive. You could mount it on Ubuntu and delete the viruses one by one.
I personally collect them...:p

---

### Post by winecurmudgeon on 2010-08-14
I think one of the problems here is the difference between a mounted drive and an unmounted USB drive. This may seem simple to someone who started when Linux was just the command line, but to those of us who have come afterward, it's a confusing concept.

Formatting a USB drive in Windows doesn't require any thinking. It still does in Linux.

---

