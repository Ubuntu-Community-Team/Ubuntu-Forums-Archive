---
title: "Disk not readable"
date: 2006-05-20
forum: General Help
---

### Post by dueyfinster on 2006-05-20
Hello all. I was flashing my iPod with Rockbox, when my computer reported (from what I can remember) a i/o segmentation fault, icons started to disappear and all applications were unstartable. The disk is not bootable and grub brings up error 17. I do not really care about my install, I just need the files on the disk.....is there any way, on a live cd to mount the drive? I tryed mounting it (based on where gparted and disks utility said it was at) but no luck, it says it is not formatted. I was also converting mp3's to ogg (with soundconverter) at the time.

Please help, I am desperate, all my precious files.,,,

Output of:

sudo fdisk -l /dev/hda 
IS:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19264   154738048+  83  Linux
/dev/sda2           19265       19452     1510110   82  Linux swap / Solaris

---

### Post by Ptero-4 on 2006-05-20
Run a S.M.A.R.T diagnostic on the disk to see if it's dead or dying. Then run fsck to see if the filesystem structure is f*ck'd up.

---

### Post by dueyfinster on 2006-05-21
First of all, thank you so much for your reply. How do I run these things? Can I do it off a livecd? As I mentioned, grub gives error 17, meaning I cannot boot off it.
[U][I][B]
S.M.A.R.T:[/B][/I][/U]
root@ubuntu:/home/ubuntu# smartctl --health /dev/sda
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Request Sense failed, [Input/output error]

_***ALSO:***_

root@ubuntu:/home/ubuntu# smartctl -a /dev/sda
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: ATA      Maxtor 6Y160M0   Version: YAR5
Serial number: Y472SJBE
Device type: disk
Local Time is: Sun May 21 15:17:03 2006 UTC
Device does not support SMART
Request Sense failed, [Input/output error]

Device does not support Error Counter logging

[GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on']
Device does not support Self Test logging

---

### Post by Ramaddan on 2007-04-23
I don't know if anyone replied to this, but just for future reference, since I was looking this up, in case anyone comes accross this.

In order to be able to properly read from the above Hard disk, which is a SATA hard disk, and as the manufacturer claim, it does support S.M.A.R.T., an option has to be added to the smartctl command: -d ata

This tells the smartctl command to read using the ata function. Usually, this is detected automatically if the hard disk is present in the smartools database.

However, this is not the case with some hard disk, such as the one above, so using any other option with smartctl, the above stated option, "-d ata" needs to be added to override automatic detection.

So the above given commands become:

> smartctl --health -d ata /dev/sda to view only health

OR

> smartctl -a -d ata /dev/sda to view everything

Make sure you replace "sda" with the appropriate name or label  of your hardisk.
You can use Gnome Partition to view all your hardisks.

Hope this helps someone in the future.

---

