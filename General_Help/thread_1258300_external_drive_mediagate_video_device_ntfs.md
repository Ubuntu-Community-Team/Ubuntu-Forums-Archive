---
title: "external drive mediagate video device ntfs"
date: 2009-09-04
forum: General Help
---

### Post by BillyPrefect on 2009-09-04
Hello.  Any help please?

Below is copy/paste from the bottom bit of "dmesg"

I can only read one directory, for some reason.  I can write to the device as it does so the free space, and after unplugging from my computer I can watch the movies just fine on the TV... but when I plug back into my pc, I can't even read the directories I made last time when I wasn't able to read.  Owner ship issues???  It is formated NTFS, 320G harddrive media player.  I can't reformat, none of my computers have the space at this point to hold the movies on it, I have 12G free out of 320, also it wouldn't matter, I can't read the drive from ubuntu.  I can finish filling it up, but why?  I am intending to buy/build a small media server, but at this point I can't even save my stuff.  

Any/all help would be very much appreciated.  Thank you.

[INDENT][11658.724143] usb 1-5: new high speed USB device using ehci_hcd and address 5
[11658.859369] usb 1-5: configuration #1 chosen from 1 choice
[11658.978634] Initializing USB Mass Storage driver...
[11658.979220] scsi2 : SCSI emulation for USB Mass Storage devices
[11658.979635] usbcore: registered new interface driver usb-storage
[11658.979642] USB Mass Storage support registered.
[11658.984056] usb-storage: device found at 5
[11658.984061] usb-storage: waiting for device to settle before scanning
[11664.984402] usb-storage: device scan complete
[11665.352461] scsi 2:0:0:0: Direct-Access     ST332062 0A               3.AA PQ: 0 ANSI: 0
[11665.355717] sd 2:0:0:0: [sdb] 625142447 512-byte hardware sectors: (320 GB/298 GiB)
[11665.372654] sd 2:0:0:0: [sdb] Write Protect is off
[11665.372661] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11665.372666] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[11665.376282] sd 2:0:0:0: [sdb] 625142447 512-byte hardware sectors: (320 GB/298 GiB)
[11665.380046] sd 2:0:0:0: [sdb] Write Protect is off
[11665.380053] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11665.380058] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[11665.380066]  sdb: sdb1
[11665.400373] sd 2:0:0:0: [sdb] Attached SCSI disk
[11665.400492] sd 2:0:0:0: Attached scsi generic sg2 type 0
[/INDENT]

---

### Post by BillyPrefect on 2009-09-04
Here is sudo fdisk -l listing
[INDENT]
Disk /dev/sdb: 320.0 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3853ab0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
[/INDENT]

---

### Post by BillyPrefect on 2009-09-04
Sorry... 

it is a 320Gb Medialink MG350NDAS device.  I have NDAS turned off, so that is not the issue.  When plugged into the TV I can see that I have pile of directories, movies, files, subdirectories, etc... filled up to the point where there is, like I said, 12G free out of 320G.  I would like to be able to read this drive like normal, see the directory structure, write, move files, delete, etc, as if I was plugged into a ms winblows machine.

---

