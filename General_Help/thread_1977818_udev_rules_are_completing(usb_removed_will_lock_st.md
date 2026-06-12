---
title: "udev rules are completing(usb removed will lock station"
date: 2012-05-10
forum: General Help
---

### Post by amdemas on 2012-05-10
Hello Everyone,

I have been trying to setup my system to when I insert a usb drive it will unlock the station and when it is removed it will lock the station. Here is my udev rule.

```

91-usbkey.rules

ACTION=="remove", SUBSYSTEM=="usb", ATTRS{serial}=="<entered serial here>", RUN+="/home/<user>/scripts/lock.sh"
ACTION=="add", SUBSYSTEM=="usb", ATTRS{serial}=="<entered serial here>", RUN+="/home/<user>/scripts/unlock.sh"

```Here is the .sh files:

```

lock.sh

#!/bin/sh

gnome-screensaver-command -l

``````

unlock.sh

#!/bin/sh

gnome-screensaver-command -d

```Here is the output in dmesg when i plug and then plug it back in:

```

[ 2339.111530] usb 2-1.2: USB disconnect, device number 4
[ 2353.118783] usb 2-1.2: new high-speed USB device number 5 using ehci_hcd
[ 2353.212456] scsi8 : usb-storage 2-1.2:1.0
[ 2354.209327] scsi 8:0:0:0: Direct-Access     SanDisk  Cruzer           8.02 PQ: 0 ANSI: 0 CCS
[ 2354.209856] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 2354.211845] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 2354.454423] sd 8:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[ 2354.455410] sd 8:0:0:0: [sdb] No Caching mode page present
[ 2354.455413] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2354.457307] sd 8:0:0:0: [sdb] No Caching mode page present
[ 2354.457316] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2354.459192]  sdb: sdb1

```Is there something I am doing wrong? Other than the udev rule number being 91 I did try changing it to 80 and 85 with still no success.

Any help would be greatly appreciated.

---

