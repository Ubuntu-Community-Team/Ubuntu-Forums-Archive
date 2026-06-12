---
title: "how to make USB bootable"
date: 2012-07-12
forum: General Help
---

### Post by psihokiller4 on 2012-07-12
I have some problems I cannot make my usb bootable and I'm sure I have  in bios bootable priority as I did it before but I don't know what I'm  doing wrong this time


and now kinda trying to follow this
[http://www.linuxquestions.org/questions/slackware-installation-40/usb-boot-stick-wont-858365/](http://www.linuxquestions.org/questions/slackware-installation-40/usb-boot-stick-wont-858365/)

```
root@military-desktop-linux:/home/military# parted /dev/sdc
GNU Parted 2.2
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)  set 1 boot on

```

```

root@military-desktop-linux:/home/military# fdisk -l /dev/sdc

Disk /dev/sdc: 4011 MB, 4011491328 bytes
124 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004369b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1019     3917005    c  W95 FAT32 (LBA)
root@military-desktop-linux:/home/military#
```

how do I make my 4GB USB bootable?

---

### Post by americanman28 on 2012-07-12
I recommend using windows to make a .ISO file bootable. Use the Universal USB Installer [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button) 
Good Luck

---

### Post by oldfred on 2012-07-12
Bios will not boot a non-bootable flash drive generally. But just putting boot flag on the partition does not make it bootable. You have to have a boot loader. Windows (and Windows like) boot loaders use code in the MBR to find which partition has the boot flag and then loads code from the partition boot sector to boot. Grub does not use boot flag but code in MBR tells it which partition to find the rest of grub to continue to boot.

So what do you want to boot? Ubuntu, Ubuntu installer, Windows installer?  Installing the boot code is different for each type of install.

---

### Post by papibe on 2012-07-12
Hi psihokiller4.

There are easier options. Here's a couple (both using GUI).

Install unetbootin from the software center. This works for all ISOs.

For an Ubuntu ISO CD you can use the already installed 'Startup Disk Creator'

I hope that helps, and let us know how it goes.
Regards.

---

### Post by flipper T on 2012-07-12
+1 for Startup Disk Creator.

used it yesterday & works a treat.

---

### Post by psihokiller4 on 2012-07-12
1. I hate windows
I'm trying to make usb ubuntu installer
I used unetbootin multiple times with failure

I want to install new LTS ubuntu on my asus eeePC and test it before I put it on this PC

later I saw I may have problem for bios that some bioses don't support more than 2GB bootable devices tried makeing 1.5GB partition fat32 and it didn't work

I saw fat32 has some problems with 4GB and made ext2 file format made an force choose on unetbootin and it didn't work

I haven't tried startup disc creater yet but I don't think it'll solve problem will trie it tomorrow for sure today I'm too tired

thanks for gr8 infos (any workarounds so that I don't need to get on windows)?

---

### Post by flipper T on 2012-07-12
you should have no problem with Startup Disk Creator. it will even put a copy of wubi.exe on the usb for you.

---

### Post by psihokiller4 on 2012-07-12
heh don't need wubi :) haven't tuched windows since hmmm 2 years now I think when I did I got mad and formated it

---

### Post by papibe on 2012-07-12
> **psihokiller4 said:**
> 
I used unetbootin multiple times with failure
That have happened to me a couple of time in 10.04, but no recently.

The way you can increase your chances is to first use gparted to delete all partitions on the USB drive, then create a new one, and finally use unetbootin on it.

Hope it helps.
Regards.

---

### Post by psihokiller4 on 2012-07-12
> **papibe said:**
> That have happened to me a couple of time in 10.04, but no recently.

The way you can increase your chances is to first use gparted to delete all partitions on the USB drive, then create a new one, and finally use unetbootin on it.

Hope it helps.
Regards.
mainly using gparted from today for this but heaing same resaults thanks will try to be more cautious that I literally use only gparted

---

### Post by psihokiller4 on 2012-07-16
tried everything with 4GB USB and nothing worked

I finally got 1GB USB found somewhere
but it still doesn't work

it's sad I know it worked before on different system I guess it just don't wanna work on ubuntu 10.04 LTS I hope that new LTS version is any better

---

