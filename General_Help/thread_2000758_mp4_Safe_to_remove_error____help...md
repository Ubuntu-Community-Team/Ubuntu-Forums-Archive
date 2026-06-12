---
title: "mp4 Safe to remove error    help.."
date: 2012-06-10
forum: General Help
---

### Post by oklokl on 2012-06-10
[http://www.ownta.com/ployer-m600-mp4-player-with-2.4-inch-tft-lcd-2gb.html](http://www.ownta.com/ployer-m600-mp4-player-with-2.4-inch-tft-lcd-2gb.html)
Model Ployer M600 MP4 Player with 2.4 inch TFT LCD - 4GB
Ubuntu 12.04

/dev/sdb1 4G
/dev/sdb2  SD Memory Card

udisks --detach /dev/sdb
The same error

[http://forums.gentoo.org/viewtopic-t-893978-start-0.html](http://forums.gentoo.org/viewtopic-t-893978-start-0.html)
emerge -1 sys-fs/udisks (No command 'emerge' found, did you mean:)


Ubuntu Nautilus  > Safe to remove mp4 error..  log

log
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6)
SYNCHRONIZE CACHE: synchronize cache(10): transport: Host_status=0x05 [DID_ABORT]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x01 [DID_NO_CONNECT]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory

---

### Post by Jose Catre-Vandis on 2012-06-10
Can you tell us what you are doing, trying to do, that is causing the error/problem?

---

### Post by oklokl on 2012-06-10
Thank you.
my mp4 Safe removal, an error occurs.

When I'm safe removal.
An error occurs.

](*,)

log.. <- Nautilus error message
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6)
SYNCHRONIZE CACHE: synchronize cache(10): transport: Host_status=0x05 [DID_ABORT]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x01 [DID_NO_CONNECT]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory


udisks --detach /dev/sdb   <- error
Detach failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


syslog
Jun 10 23:06:06 kde dbus[717]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 10 23:06:06 kde dbus[717]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 10 23:07:37 kde kernel: [ 1882.232030] usb 1-5: new high-speed USB device number 4 using ehci_hcd
Jun 10 23:07:37 kde mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5"
Jun 10 23:07:37 kde mtp-probe: bus: 1, device: 4 was not an MTP device
Jun 10 23:07:37 kde kernel: [ 1882.398558] Initializing USB Mass Storage driver...
Jun 10 23:07:37 kde kernel: [ 1882.398989] usb-storage 1-5:1.0: Quirks match for vid 071b pid 3203: 80600
Jun 10 23:07:37 kde kernel: [ 1882.399049] scsi4 : usb-storage 1-5:1.0
Jun 10 23:07:37 kde kernel: [ 1882.399187] usbcore: registered new interface driver usb-storage
Jun 10 23:07:37 kde kernel: [ 1882.399190] USB Mass Storage support registered.
Jun 10 23:07:37 kde kernel: [ 1882.430207] usbcore: registered new interface driver uas
Jun 10 23:07:38 kde kernel: [ 1883.396637] scsi 4:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
Jun 10 23:07:38 kde kernel: [ 1883.396958] scsi 4:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
Jun 10 23:07:38 kde kernel: [ 1883.398023] sd 4:0:0:0: Attached scsi generic sg3 type 0
Jun 10 23:07:38 kde kernel: [ 1883.402340] sd 4:0:0:0: [sdb] 7569408 512-byte logical blocks: (3.87 GB/3.60 GiB)
Jun 10 23:07:38 kde kernel: [ 1883.402348] sd 4:0:0:0: [sdb] Assuming Write Enabled
Jun 10 23:07:38 kde kernel: [ 1883.402353] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jun 10 23:07:38 kde kernel: [ 1883.403203] sd 4:0:0:0: [sdb] Assuming Write Enabled
Jun 10 23:07:38 kde kernel: [ 1883.403208] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jun 10 23:07:38 kde kernel: [ 1883.404741]  sdb: sdb1
Jun 10 23:07:38 kde kernel: [ 1883.405366] sd 4:0:0:0: [sdb] Assuming Write Enabled
Jun 10 23:07:38 kde kernel: [ 1883.405371] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jun 10 23:07:38 kde kernel: [ 1883.405377] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jun 10 23:07:38 kde kernel: [ 1883.406577] sd 4:0:0:1: Attached scsi generic sg4 type 0
Jun 10 23:07:38 kde kernel: [ 1883.412562] sd 4:0:0:1: [sdc] 61315072 512-byte logical blocks: (31.3 GB/29.2 GiB)
Jun 10 23:07:38 kde kernel: [ 1883.412568] sd 4:0:0:1: [sdc] Assuming Write Enabled
Jun 10 23:07:38 kde kernel: [ 1883.412572] sd 4:0:0:1: [sdc] Assuming drive cache: write through
Jun 10 23:07:38 kde kernel: [ 1883.415430] sd 4:0:0:1: [sdc] Assuming Write Enabled
Jun 10 23:07:38 kde kernel: [ 1883.415435] sd 4:0:0:1: [sdc] Assuming drive cache: write through
Jun 10 23:07:38 kde kernel: [ 1883.418482]  sdc: sdc1
Jun 10 23:07:38 kde kernel: [ 1883.419617] sd 4:0:0:1: [sdc] Assuming Write Enabled
Jun 10 23:07:38 kde kernel: [ 1883.419622] sd 4:0:0:1: [sdc] Assuming drive cache: write through
Jun 10 23:07:38 kde kernel: [ 1883.419626] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jun 10 23:09:13 kde kernel: [ 1977.936030] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Jun 10 23:09:13 kde kernel: [ 1978.089338] WARNING! power/level is deprecated; use power/control instead
Jun 10 23:09:13 kde kernel: [ 1978.095689] usb 1-5: USB disconnect, device number 4


Occasionally.... eject working order . 
But
It takes a long time.
Message Output


Is a fat32 partition.
mp4 does not remove   (eject error)
I must be removed forcibly.

---

### Post by sudodus on 2012-06-10
> **oklokl said:**
> Thank you.
my mp4 Safe removal, an error occurs.

When I'm safe removal.
An error occurs.

](*,)

log.. <- Nautilus error message
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6)
SYNCHRONIZE CACHE: synchronize cache(10): transport: Host_status=0x05 [DID_ABORT]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x01 [DID_NO_CONNECT]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory



Is a fat32 partition.
mp4 does not remove   (eject error)
I must be removed forcibly.

Have you tried to unmount the partition with the command umount? If /dev/sdb partitions 1 and 2 are mounted, try
```
sudo umount /dev/sdb1
sudo umount /dev/sdb2
```
Then check with ```
df
``` if something on /dev/sdb is still mounted!

---

### Post by oklokl on 2012-06-10
umount, are well used.

umount -l /dev/sdb1
umount -l /dev/sdb2
udisks --unmount /dev/sdb1
udisks --unmount /dev/sdb2
udisks --unmount /dev/sdXy
ok..

But I
 I want to remove a safe.

---

### Post by sudodus on 2012-06-10
> **oklokl said:**
> umount, are well used.

umount -l /dev/sdb1
umount -l /dev/sdb2
udisks --unmount /dev/sdb1
udisks --unmount /dev/sdb2
udisks --unmount /dev/sdXy
ok..

But I
 I want to remove a safe.
Maybe I don't understand. My main language is not English, so please explain in detail!

If I understand correctly, lazy unmount succeeds.

- Does normal unmount work? That is umount without -l ?

- Are there open files or is there a process with its working directory on a partition on the mp4 player? In that case, close the file(s) and stop the process or if it is a terminal window, change directory!

If normal unmount works, and you cannot see the drive with [FONT="Courier New"][SIZE="3"]df[/SIZE][/FONT], that means that any read/write process should have finished, and that it is safe to remove the drive.

---

### Post by oklokl on 2012-06-10
Thank you.
 I would like a safer and more ..
 I'd like to close(LED off) usb.

umount / dev / sdb
Forced to remove.
In fact, the data has been corrupted.

umount-l / dev / sdb
Because it was safe ...


df (normal removal is complete).
Complete shutdown system does not work
eject.....     mp4..  
If I do not off LED... 


I have experience with partition corruption.

---

### Post by sudodus on 2012-06-10
> **oklokl said:**
> Thank you.
 I would like a safer and more ..
 I'd like to close(LED off) usb.

umount / dev / sdb
Forced to remove.
In fact, the data has been corrupted.

umount-l / dev / sdb
Because it was safe ...

If you try to unmount normally without -l, it won't succeed if it is busy. So the partition is still mounted. You can force unmount with -f but I think it is a bad idea. My experience is that if you unmount normally and it succeeds, there is no file corruption (it should show in the terminal output, check with df to be sure).

If you had file corruption, maybe the normal unmount failed, but you did not notice it.

Lazy unmount detaches the filesystem from the filesystem hierarchy at once, and cleans up all references to the filesystem as soon as it is not busy anymore. The problem is how to know, when the clean-up has finished, so that you can pull out the USB plug.

Anyway, if your device will not be properly unmounted and safe to remove with the standard (automatic) procedure in the file browser, you can create a script or alias to make it fairly convenient to use terminal commands.

---

### Post by oklokl on 2012-06-10
Thank you very much.   n,.n;;
I hope this is resolved the bug is.

my bash 

#!/bin/bash
umount -l /dev/sdb1
umount -l /dev/sdb2
udisks --unmount /dev/sdb1
udisks --unmount /dev/sdb2

---

