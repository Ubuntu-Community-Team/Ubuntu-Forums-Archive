---
title: "Mounting RAID from live CD"
date: 2010-08-21
forum: General Help
---

### Post by Maletor on 2010-08-21
I have three partitions, /boot (RAID1), swap(RAID1) and root(RAID5). As far as I know I need to boot into the live CD and mount them and somehow start up the array and chroot into that.

The whole reason I need to do this is because I do not want my LVM anymore. I need to umount /var and I can't do that while I'm running the system... right?

So what steps do I need to take to mount my devices and chroot into them and remove my LVM (while preserving my data)? 

Also I have an error from trying to mount /dev/sda1 to /mnt/sda1

```

ubuntu@ubuntu:~$ sudo dmesg | tail
[  269.140843] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_OK
[  269.140845] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 02 f8 00 00 00 08 00
[  269.140850] end_request: I/O error, dev sda, sector 194560
[  269.140853] Buffer I/O error on device sda2, logical block 0
[  337.430839] sd 2:0:0:0: timing out command, waited 180s
[  337.430842] sd 2:0:0:0: [sda] Unhandled error code
[  337.430843] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_OK
[  337.430845] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 02 f7 80 00 00 08 00
[  337.430849] end_request: I/O error, dev sda, sector 194432
[  337.430851] Buffer I/O error on device sda1, logical block 24048

```

---

