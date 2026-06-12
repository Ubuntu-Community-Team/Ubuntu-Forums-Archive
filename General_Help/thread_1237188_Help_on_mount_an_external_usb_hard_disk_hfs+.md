---
title: "Help on mount an external usb hard disk hfs+"
date: 2009-08-11
forum: General Help
---

### Post by karimone on 2009-08-11
Hi all, I have a Mac Mini PPC that I use as server with Ubuntu Server 9.04 PPC. Of course the computer have no monitor and I use it just by terminal with ssh. Now I have to transfer 45GB and I attached my external usb hard disk to the mac mini. The hard disk has severals partitions in hfs format but really I don't know how to mount that

Dmesg: 

```
[   13.690989] Driver 'sd' needs updating - please use bus_type methods
[   13.694738] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   13.696487] sd 0:0:0:0: [sda] Write Protect is off
[   13.696495] sd 0:0:0:0: [sda] Mode Sense: 21 00 00 00
[   13.696499] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   13.697458] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   13.698196] sd 0:0:0:0: [sda] Write Protect is off
[   13.698200] sd 0:0:0:0: [sda] Mode Sense: 21 00 00 00
[   13.698203] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   13.698403]  sda:<6>cfg80211: Calling CRDA to update world regulatory domain

```

And more:

```
[   14.793670] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   17.297698]  sda1
[   17.298166] sd 0:0:0:0: [sda] Attached SCSI disk
[   17.371172] sd 0:0:0:0: Attached scsi generic sg0 type 0

```

If a try to mount:

```
karim@Marty:/mnt$ sudo mount -t hfs /dev/sda1 /mnt/usb-storage/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

karim@Marty:/mnt$ sudo mount -t hfsplus /dev/sda1 /mnt/usb-storage/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The problem is that I don't know the exact dev name for every partition and if I try to mount I get always the error of wrong fs type. Any idea?

Thanks in advance

---

### Post by tomdkat on 2009-08-24
Can you connect the external hard drive to a working Mac to make sure it can mount the drive ok?

Also, what happens if you leave the filesystem off of the mount command?

Peace...

---

### Post by karimone on 2009-08-25
Worked and I say worked 'cause the fastet solution was to format the external hard disk.

Thanks for the interest.

---

