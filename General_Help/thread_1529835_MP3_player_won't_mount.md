---
title: "MP3 player won't mount"
date: 2010-07-12
forum: General Help
---

### Post by Dex73 on 2010-07-12
I have a SANSA FUZE that will mount on a computer with hardy but not with lucid. The problem is I really only need it to work in lucid. I've tried following the online tutorials but I'm not sure I'm doing it right.

running lsusb gives...
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 020: ID 0781:74c2 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Hopefully this is as simple as me not knowing what I'm doing. I need help.

---

### Post by Dex73 on 2010-07-13
Can anyone at least tell me the correct command? When I use the other computer it recognizes it as "SANSA FUZE".

Also, I tried these 3 commands...
$ sudo fdisk -l
[sudo] password for one: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001d49b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19087   153312256   83  Linux
/dev/sda2           19087       19458     2975745    5  Extended
/dev/sda5           19087       19458     2975744   82  Linux swap / Solaris

$ sudo mount -t vfat /dev/sda4 /media/SANSA_FUZE -o uid=1000,gid=100,utf8,dmask=027,fmask=137
mount: special device /dev/sda4 does not exist
one@one-laptop:~$ sudo mount -t vfat /dev/sda2 /media/SANSA_FUZE -o uid=1000,gid=100,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ sudo mount -t vfat /dev/sda3 /media/SANSA_FUZE -o uid=1000,gid=100,utf8,dmask=027,fmask=137
mount: special device /dev/sda3 does not exist

$ sudo mount -t vfat /dev/sda5 /media/SANSA_FUZE -o uid=1000,gid=100,utf8,dmask=027,fmask=137
mount: /dev/sda5 already mounted or /media/SANSA_FUZE busy

---

### Post by MooPi on 2010-07-13
Try another usb port, or plug in the device after initial boot and not during,  let me know if you have a response from your machine from either. Each attempt open a terminal and use ```
sudo fdisk -l
```Have you had any luck with any usb device from your lucid install ?

---

### Post by Dex73 on 2010-07-13
All of my other devices are working fine, and switching the ports doesn't change the output. It's always

$ sudo fdisk -l
[sudo] password for one: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001d49b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19087   153312256   83  Linux
/dev/sda2           19087       19458     2975745    5  Extended
/dev/sda5           19087       19458     2975744   82  Linux swap / Solaris

Also, if I just leave it plugged in a start up the MP3 player messes up. It'll say Connected on the MP3 players screen even after you unplug it. You then have to let the battery die to reset it.

---

### Post by Schrute Farms on 2010-07-13
Start Rhythmbox in Lucid with your player plugged in & see if it shows as a device there.  If it does then you are in MTP mode.  My drive did not mount in MTP mode, only in MSC mode.  But it did show as a device in MTP.

If it does show in Rhythmbox then you will have to change your USB mode to make the player mount.  Go to Settings/System Settings/USB mode on your Fuze, then change from MTP to MSC.  Then plug it in & see if it mounts.  If it works, then you would have to switch the mode back, copy everything on it to your drive, change the mode back again & re-copy everything back to the player.

I've never used this player in Hardy, but I had no problems in Lucid with mine.  I originally used MSC mode (Showing it as a player, not a drive).  It worked in Lucid that way, but it didn't in Koala (My desktop wouldn't run Lucid correctly), so I had to change modes to make it show as a drive.  Because things put on the player in one mode doesn't show in the other, I had to copy music off, change the mode, then copy them back.

---

### Post by Schrute Farms on 2010-07-13
Also, regarding your Fuze locking up, if you hold the power button on for like 30-40 seconds when it's locked up, it will reset.

---

### Post by Dex73 on 2010-07-13
It's working great now! It showed in Rhythembox so I cheeked out the settings. I had it on automatic mode so I changed it to MSC. Don't even need to copy files. I feel so lucky!

---

