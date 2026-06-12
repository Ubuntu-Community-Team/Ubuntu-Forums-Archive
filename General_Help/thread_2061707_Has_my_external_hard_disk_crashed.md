---
title: "Has my external hard disk crashed?"
date: 2012-09-23
forum: General Help
---

### Post by arroy_0209 on 2012-09-23
I have two ext hard drives(disks) out of which one is fine. When I add the cable at the proper slot, a window opens in ubuntu 10.04, and the contents are displayed. The other however, is not opened automatically by the OS (though the indicator light on Ext HDD is on) and the systems log file for messages shows these entries:

```

usb 1-6: new high speed USB device using ehci_hcd and address 3
usb 1-6: configuration #1 chosen from 1 choice
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.

scsi 2:0:0:0: Direct-Access     Hitachi  HTS541680J9AT00       PQ: 0 ANSI: 0

sd 2:0:0:0: Attached scsi generic sg2 type 0

sd 2:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)

sd 2:0:0:0: [sdb] Write Protect is off
 sdb: sdb1
sd 2:0:0:0: [sdb] Attached SCSI disk

```
each starts with a part related to kernel (e.g., the first starts with kernel: [  124.200077]) which I had not shown here. From these it appears that the OS is able to recognize the ext HDD but unable to open it. Is there any way I can solve this?

---

### Post by MC_Claus on 2012-09-23
Have you tried mounting it manually?

```
sudo mount /dev/sdb1 /<some>/<dir>
```

It might give your an idea if it works or not.

If mount gives you error perhaps try to run
```
fsck /dev/sdb
```
to check the disk for errors.

---

### Post by arroy_0209 on 2012-09-24
I tried sudo fsck /dev/sdb and the result is:
```

fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
Following the suggestion I had tried: sudo e2fsck -b 8193 /dev/sdb and the result is:
```

e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such file or directory while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
No improvement unfortunately. So is the ext hard disk permanently damaged? (I was unable to use the command sudo mount /dev/sdb1 /<some>/<dir> since I am not sure what to use for /<some>/<dir>)

---

### Post by einonm on 2012-09-24
> **MC_Claus said:**
> 

If mount gives you error perhaps try to run
```
fsck /dev/sdb
```
to check the disk for errors.

That needs to be :

```
fsck /dev/sdb1
```

The '1' specifies the filesystem, not the device.

---

### Post by einonm on 2012-09-24
> **arroy_0209 said:**
> I was unable to use the command sudo mount /dev/sdb1 /<some>/<dir> since I am not sure what to use for /<some>/<dir>)

You can use any dir that doesn't already have a mount on it, so for example:

```
mkdir ~/tempdir
sudo mount /dev/sdb1 ~/tempdir
ls ~/tempdir
```

Should mount and list the contents of the device.

---

