---
title: "Cant find my work in MNT/WINDRIVE"
date: 2010-01-05
forum: General Help
---

### Post by james_holiday on 2010-01-05
[SIZE=2]Hey I have a windows xp and recently suffered from the dreaded 'freezes at system.mup' problem upon booting my computer..[/SIZE]
 
[SIZE=2]Unfortunately I couldnt do a repair install so I decided to do a multi boot, and install windows again on my system.. I did this multi boot on Partition1..[/SIZE]
 
[SIZE=2]When I started doing the multi boot, the installation never completed and I got the blue screen of death.[/SIZE]
 
[SIZE=2]I'm now using Ubuntu (which has been helpful so far) to salvage some pictures and work and thanks to this link [http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/](http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/) [/SIZE]
[SIZE=2]I've got up to file system/the mnt/ windrive folder.. Okay this is what I see....[/SIZE]
[SIZE=2]System Volume Info, boot.ini, bootex.log, Ntdect.com, ntldr and WINDOWS[/SIZE]
 
 
[SIZE=2]I went into WINDOWS and this is what I found....[/SIZE]
[SIZE=2]addins, appPatch, config, connection wizard, cursors, debug, dell, driver cache, fonts, help, ime, inf, java, media, msagent, msapps, mui, pchealth, peernet, provisioning, repair, resources, security, system, system32, temp, twain_32, web, winSxS...etc[/SIZE]
 
 
[SIZE=2]Okay.. so am I suppose to see this?? Does anyone know where my work and personal folders are hiding??[/SIZE]
 
[SIZE=2]I'm not sure whether or not my work and pictures have been wiped or installed over... If I was doing a multi boot it probably shouldnt have..[/SIZE]
[SIZE=2]Any ideas or help??[/SIZE]
 
[SIZE=2]Please help, this is quite urgent, I need to get back to work..[/SIZE]
 
[SIZE=2]Cheers[/SIZE]

---

### Post by pastalavista on 2010-01-05
I believe what you see there is the Windows restore partition. Open a terminal (Applications--> Accessories--> Terminal) and enter this ```
sudo fdisk -l
```and post the output here.

---

### Post by james_holiday on 2010-01-05
Hey, thanks for replying quickly..
 
It says...
 
fdisk: Invalid option - - '1'
 
Usage; fdisk [-b SSZ] [-u] DISK Change partition table
fdisk -l [-b SSZ] [-u] DISK List Partition Tables(s)
fdisk -s PARTITION Give Partition size(s) in blocks
fdisk -v Give fdisk version
 
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give start and endin sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors 
 
 
 
What do you think??

---

### Post by pastalavista on 2010-01-05
It is fdisk -l (lower case L) not 1

---

### Post by BitJunkie on 2010-01-05
The option after fdisk is not a one, it is a lowercase L. Try again. :)

---

### Post by pricetech on 2010-01-05
> **james_holiday said:**
> Hey, thanks for replying quickly..
 
It says...
 
fdisk: Invalid option - - '1'
 


That should be a lower case ell, not a number one.

What you're looking for, once you get the right partition mounted, is a Documents and Settings folder inside of which you should find a folder with your winders username.  Your stuff is in there, mostly in My Documents.

NOTE that this is assuming you put stuff where winders wants to put it by default.

---

### Post by james_holiday on 2010-01-05
Okay I did sudo fdisk -l
 
And this is what I got...
 
 
Disk /dev/sda: 40.0 GB, 400077619920 bytes
255 heads, 63 sectors/track, 48864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11811180
 
Device Boot        Start    End     Block       Id    System
/dev/sda1 *            1    4863   39062016  7     HPFS/NTFS
 
 
What do I do now??
How do I mount the right partition?

---

### Post by pricetech on 2010-01-05
I only see one partition so it looks like you wiped your winders when you attempted to repair.

---

