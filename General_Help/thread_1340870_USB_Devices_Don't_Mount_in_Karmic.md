---
title: "USB Devices Don't Mount in Karmic"
date: 2009-11-29
forum: General Help
---

### Post by Unanimated on 2009-11-29
I recently did a clean install of Karmic to fix a problem like this, only right before I did the install Karmic wasn't mounting any disk except for the main one. And I want to note that before I did the reinstall, USB storage devices worked perfectly and always mounted without fail and then ran just fine afterwards. Now, after the install, my other hard drive mounts fine.

However, after the clean install (it should be similar to last time, I copied over my /home folder from my previous installation into the new one) USB devices quit mounting. I have a Sandisk Sansa Fuze 8GB that used to mount perfectly and a generic MobileMate flash drive that's apparently from Sandisk. There's nothing wrong with the cord of the Fuze or the port that it's plugged into, and the USB mode is set to MSC. I know that there's nothing wrong with the flash drive because my motherboard's BIOS shows it when it's running the tests, and also because I apparently have a bootable Karmic live CD on there and that boots from USB when there's nothing else available to boot from. What's Karmic's suddenly acquired issue, and how can I solve it? I just got a bunch of music that I wanted to copy over to my Fuze before I went to bed tonight, too. ):

---

### Post by Unanimated on 2009-11-29
Also, here's the lsusb output when the player and flash drive are plugged in:
```
sam@sam-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0781:74c3 SanDisk Corp. 
Bus 001 Device 006: ID 0781:5158 SanDisk Corp. 
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Unanimated on 2009-11-30
bump

---

### Post by darkreaction on 2009-12-02
ya I am having the same problem.

---

### Post by sovesky on 2009-12-07
So do I.
The difference is that it mounts Sansa Fuze correctly, but not the Micro SD built into the Fuze.
> 
Bus 001 Device 010: ID 0781:74c1 SanDisk Corp. Sansa Fuze (msc)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 002: ID 03f0:8104 Hewlett-Packard Printing Support
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by okubax on 2009-12-07
Same Here. The "devicekit-disks" update messed things up. Downgrading to the earlier version fixes the issue

---

### Post by OmegaBLK on 2009-12-07
Been having this issue as well since upgrading to Karmic.  First my ipod would not mount now after the latest update none of my usb devices will mount unless I connect two of them at a time--after plugging the second usb device both will get mounted.  I will check into downgrading devicekit-disks.  Does anyone know if a bug report has been filed for this yet?  I want to monitor the progress of devs fixing this issue.

---

### Post by john newbuntu on 2009-12-07
As a workaround, have you tried manually mounting the drives.
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by varangian on 2009-12-08
Don't know if there's a connection but I've just a system update come through and suddenly my USB drive is not mounting automatically. It's being detected OK:

[ 5524.473882] scsi15 : SCSI emulation for USB Mass Storage devices
[ 5524.473987] usb-storage: device found at 13
[ 5524.473989] usb-storage: waiting for device to settle before scanning
[ 5529.470229] usb-storage: device scan complete
[ 5529.470714] scsi 15:0:0:0: Direct-Access     Kingston DT Mini Slim     1.00 PQ: 0 ANSI: 2
[ 5529.471080] sd 15:0:0:0: Attached scsi generic sg4 type 0
[ 5529.473213] sd 15:0:0:0: [sdd] 7818240 512-byte logical blocks: (4.00 GB/3.72 GiB)
[ 5529.474327] sd 15:0:0:0: [sdd] Write Protect is off
[ 5529.474331] sd 15:0:0:0: [sdd] Mode Sense: 23 00 00 00
[ 5529.474334] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[ 5529.476451] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[ 5529.476457]  sdd:
[ 5529.656954] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[ 5529.656959] sd 15:0:0:0: [sdd] Attached SCSI removable disk

Mounting it manually worked but automounting is gone, for the moment at least. For completeness I also got this:

[ 4396.408553] gnome-terminal[3393]: segfault at 7fe1015c0d9a ip 00007fe109192687 sp 00007fffd1d41f10 error 7 in libpangoft2-1.0.so.0.2600.0[7fe10917b000+27000]

when starting a terminal to investigate the problem. Came up OK with the next launch otherwise things would have kind of awkward.

---

### Post by Koala Kid on 2009-12-09
same here... the latest update screwed the automounting.
anybody ?

---

### Post by napzilla on 2009-12-19
I'm having the same issue here. I could connect to my Sansa Fuze without any problems on Intrepid and Jaunty, but in Karmic it doesn't work. I also noticed that the external USB drives that I use (one's a Maxtor and one's a Seagate) don't mount the way that they used to. Whereas I used to be able to specify their name, now they mount as a string of characters. I don't know whether this is related to the issue with my Sansa. I've also noticed this on both my office and my home computer, so whatever the issue is, it's not the computer. I'll keep looking to see if I can find anything else out.

](*,)

*Update: After looking around a bit, I tried changing the USB Mode from "Auto Detect" to "MSC." Now it mounts the main device, but not the micro SD card inside it.*
*After a minute or two, it mounted the micro SD card, too.*

---

### Post by wsscott on 2009-12-23
I have a Sansa Fuze and had the same problem.  I did a firmware upgrade to 2.28 from the Sansa website using a Windows laptop.  I then changed the Sansa Fuze usb mode to MSC.   After that, the Sansa Fuze was recognized by Ubuntu 9.10 and Rhythmbox started.

---

