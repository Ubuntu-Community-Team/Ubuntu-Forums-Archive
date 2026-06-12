---
title: "Mp3 player not mounting"
date: 2006-06-29
forum: General Help
---

### Post by JoshHendo on 2006-06-29
My mpe player doesn't seem to be mounting currently. The other day it was fine, but when I went to plug it in now, on the screen it says that it is connected, but it simply doesn't mount. Any suggestions? Thanks.

(It is a Creative MuVo^2FM)

---

### Post by tubo on 2006-06-29
first of all, have a look whether the kernel picks it up correctly, type in a terminal shortly after plugging in your player:

dmesg

and post your USB related output on the board.

best
Emanuel

---

### Post by JoshHendo on 2006-06-29
[QUOTE=tubo]first of all, have a look whether the kernel picks it up correctly, type in a terminal shortly after pluffing in your player:

dmesg

and post your USB related output on the board.

best
Emanuel[/QUOTE]
```

[17182130.504000] usb 5-3: new high speed USB device using ehci_hcd and address 4
[17182130.636000] scsi3 : SCSI emulation for USB Mass Storage devices
[17182130.636000] usb-storage: device found at 4
[17182130.636000] usb-storage: waiting for device to settle before scanning
[17182135.636000]   Vendor: CREATIVE  Model: MuVo^2 FM (uHDD)  Rev: 0001
[17182135.636000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17182135.636000] SCSI device sda: 9726559 512-byte hdwr sectors (4980 MB)
[17182135.636000] sda: Write Protect is off
[17182135.636000] sda: Mode Sense: 0b 00 00 08
[17182135.636000] sda: assuming drive cache: write through
[17182135.640000] SCSI device sda: 9726559 512-byte hdwr sectors (4980 MB)
[17182135.644000] sda: Write Protect is off
[17182135.644000] sda: Mode Sense: 0b 00 00 08
[17182135.644000] sda: assuming drive cache: write through
[17182135.644000]  sda: unknown partition table
[17182138.432000] sd 3:0:0:0: Attached scsi removable disk sda
[17182138.432000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17182138.444000] usb-storage: device scan complete

```

---

### Post by trent dillman on 2006-06-29
[17182135.644000]  sda: unknown partition table

First, try rebooting with it in the usb port. If that won't work, try reformatting it.

---

### Post by JoshHendo on 2006-06-29
[QUOTE=trent dillman][17182135.644000]  sda: unknown partition table

First, try rebooting with it in the usb port. If that won't work, try reformatting it.[/QUOTE]
Tried rebooting with it in, it detected it and didn't bring up that message, but it still didn't mount it.

Unpligged and plugged it in again, and it came up that message again. I will format it soon.

BTW, do you know of any firmware like rockbox that I can put on it (rockbox doesn't support creative players I don't think :/), with a ext parition :p?

---

### Post by trent dillman on 2006-06-29
I don't know anything about changing the firmware, but if you find something that will allow me to play oggs on my MuVo TX FM, let me know. :-)

---

### Post by Arisna on 2006-06-29
Alright, I've got a hunch.  Bear with me for a minute. :) 

Terminal time.  Fire up your terminal program of choice.

```
sudo mkdir /media/musicplayer
sudo mount /dev/sda1 /media/musicplayer
```

It probably won't work.  Play with flags to the mount command if necessary to make sure it fails due to not knowing what /dev/sda1 is.  But now, hit the up arrow key and re-enter that second command.  Chances are decent that entering the command the first time will force your system to take a closer look at that partition table, and it may work now.  If it does, then something may have gone wrong with your HAL setup.  I've had that problem with my media card reader.  If not, then I'm out of ideas, but it was just one more thing to try before formatting the device.

---

### Post by JoshHendo on 2006-06-29
[QUOTE=Arisna]Alright, I've got a hunch.  Bear with me for a minute. :) 

Terminal time.  Fire up your terminal program of choice.

```
sudo mkdir /media/musicplayer
sudo mount /dev/sda1 /media/musicplayer
```

It probably won't work.  Play with flags to the mount command if necessary to make sure it fails due to not knowing what /dev/sda1 is.  But now, hit the up arrow key and re-enter that second command.  Chances are decent that entering the command the first time will force your system to take a closer look at that partition table, and it may work now.  If it does, then something may have gone wrong with your HAL setup.  I've had that problem with my media card reader.  If not, then I'm out of ideas, but it was just one more thing to try before formatting the device.[/QUOTE]
```

josh@c1:~$ sudo mount /dev/sda1 /media/usbdisk
mount: you must specify the filesystem type
josh@c1:~$ sudo mount /dev/sda1 /media/usbdisk
mount: you must specify the filesystem type
josh@c1:~$ sudo mount /dev/sda1 /media/usbdisk/ -t vfat -o iocharset=utf8,umask=000
mount: special device /dev/sda1 does not exist
josh@c1:~$

```

I will backup all my files in Windows and then format it :)

Last time I formatted it I had to send it back for a replacement :/

---

### Post by JoshHendo on 2006-06-30
I have formatted it (I booted into Windows and copied all my songs accross) and it works fine now.

Thanks! :)

---

