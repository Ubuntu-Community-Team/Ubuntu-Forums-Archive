---
title: "usb stick not shown"
date: 2009-11-11
forum: General Help
---

### Post by weissnich on 2009-11-11
My usb stick works with Win XP, but is not recognized with Ubuntu 9.10.
It is a cruzer micro 16GB stick,
lsusb shows ```
Bus 001 Device 006: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
```.

The light of the flash drive is on, how can I work out why it is not shown up?

---

### Post by brujoand on 2009-11-11
If you create a directory  and mount it there that should work, something like this in terminal

```

sudo mkdir /media/usb
sudo mount /dev/sdb1/ /media/usb

```

Assuming that the device will be called sdb, since your hdd is usually sda, and that you are trying to access the first partition on the usb stick.

---

### Post by weissnich on 2009-11-11
Doesn't work like this , syslog says:

```
Nov 11 16:02:38 ubuntu-desktop kernel: [ 4352.618368] usb-storage: device found at 6
Nov 11 16:02:38 ubuntu-desktop kernel: [ 4352.618372] usb-storage: waiting for device to settle before scanning
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.616191] usb-storage: device scan complete
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.616673] scsi 4:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.618407] sd 4:0:0:0: Attached scsi generic sg2 type 0
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.621656] sd 4:0:0:0: [sdb] 31301631 512-byte logical blocks: (16.0 GB/14.9 GiB)
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.622133] sd 4:0:0:0: [sdb] Write Protect is off
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.622139] sd 4:0:0:0: [sdb] Mode Sense: 45 00 00 08
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.622145] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.624154] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.624163]  sdb: sdb1
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.630509] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Nov 11 16:02:43 ubuntu-desktop kernel: [ 4357.630519] sd 4:0:0:0: [sdb] Attached SCSI removable disk
```

---

### Post by brujoand on 2009-11-11
Ok, so is there anything inside /media/usb now?

---

### Post by weissnich on 2009-11-11
No, this was before I tried your solution, the error I get with your solution is that I have to specify a data system type, my stick is fat32.

---

### Post by brujoand on 2009-11-11
ok, try ```
 sudo mount -t fat32 /dev/sdb1 /media/usb 
```
instaed

---

### Post by weissnich on 2009-11-11
> **GrimmVarg said:**
> ok, try ```
 sudo mount -t fat32 /dev/sdb1 /media/usb 
```
instaed

It says now, unkown data system fat32.

---

### Post by arnab_das on 2009-11-11
i think even i'm facing the same problem. it doesnt recognise the usb devices when they're plugged in permanently, but when i unplug and plug it again, it detects it.

---

### Post by weissnich on 2009-11-11
I plugged it in and unplugged it several times, no change, I tried another usb stick with 2GB, this works without problems, but I had this 16gb working with ubuntu before, this may be a problem with 9.10 ?

---

### Post by weissnich on 2009-11-11
This is what fdisk shows:

```
Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1        1955    15641929   1c  Verst. W95 FAT32 (LBA)
```

Verst. means hidden, why is it hidden???

---

### Post by anaconda on 2009-11-11
> **GrimmVarg said:**
> ok, try ```
 sudo mount -t fat32 /dev/sdb1 /media/usb 
```
instaed

I think it is 
-t vfat

and not -t fat32

So try to mount it with 
sudo mount -t vfat /dev/sdb1 /media/usb

The system seems to recognize your usb-stick, At least based on your fdisk -output.

---

### Post by weissnich on 2009-11-11
Thanks,

output is

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       
```

---

### Post by weissnich on 2009-11-11
This stick was working before with ubuntu, why it isn't now I don't know,
maybe the kernel?? dmesg shows:

```
[ 6772.872791] sd 6:0:0:0: [sdb] 31301631 512-byte logical blocks: (16.0 GB/14.9 GiB)
[ 6772.879451] sd 6:0:0:0: [sdb] Write Protect is off
[ 6772.879459] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 6772.879465] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6772.882407] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6772.882416]  sdb: sdb1
[ 6772.885406] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6772.885416] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 8046.416501] FAT: invalid media value (0x07)
[ 8046.416509] VFS: Can't find a valid FAT filesystem on dev sdb1.

```

---

### Post by anaconda on 2009-11-12
What I would do:

If the USB-stick still works somewhere, eg. in windows, then backup the data,

And reformat the stick in ubuntu. After that you can copy the data back to the stick, and it should work normally.

I have experience of one usb-stick, which had an "illegal" partition table, but it did work in windows. After I repartitioned and formatted it in ubuntu it worked everywhere.

---

