---
title: "unable to mount the SD card"
date: 2012-04-01
forum: General Help
---

### Post by azertyh on 2012-04-01
hello,

i have a SD card where are my photos. i want to copy the photos in my harddrive. i can't mount it. some commands list the SD card, others not.

when the SD card is inserted :
```
azertyh@vostro-1015:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:20f5 Quanta Computer, Inc. 
Bus 003 Device 002: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 006 Device 003: ID 5136:4678  
```
i think the last line is the SD card because when i unplug it, this last line doesn't appear.

the dmesg, just after SD card plugged :
```
[ 2035.472067] usb 6-2: new full speed USB device number 3 using uhci_hcd
[ 2035.648371] scsi7 : usb-storage 6-2:1.0
[ 2038.556394] scsi 7:0:0:0: Direct-Access     USB2.0   CARD-READER      1.01 PQ: 0 ANSI: 2
[ 2038.561284] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 2038.571129] sd 7:0:0:0: [sdb] Attached SCSI removable disk
```

blkid and fdisk don't detect the SD card :
```
azertyh@vostro-1015:~$ sudo blkid
[sudo] password for azertyh: 
/dev/sda1: UUID="ce9e4639-0f86-4279-a6e4-b781b0d9ba4c" TYPE="ext4" 
/dev/sda5: UUID="d4607ed6-bce7-4129-9f2a-e828f22f0619" TYPE="swap" 
```

```
azertyh@vostro-1015:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique)*: 512*octets / 512*octets
taille d'E/S (minimale / optimale)*: 512*octets / 512*octets
Identifiant de disque*: 0x0002bd20

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *        2048   618924031   309460992   83  Linux
/dev/sda2       618926078   625141759     3107841    5  Étendue
/dev/sda5       618926080   625141759     3107840   82  partition d'échange Linux / Solaris

```

but sudo lshw and ls -la /dev/sd* detect it :
```
*-scsi
          physical id: 1
          bus info: usb@7:2
          logical name: scsi9
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/sdb
```

```
ls -la /dev/sd*
brw-rw---- 1 root disk 8,  0 2012-03-31 18:27 /dev/sda
brw-rw---- 1 root disk 8,  1 2012-03-31 18:27 /dev/sda1
brw-rw---- 1 root disk 8,  2 2012-03-31 18:27 /dev/sda2
brw-rw---- 1 root disk 8,  5 2012-03-31 18:27 /dev/sda5
brw-rw---- 1 root disk 8, 16 2012-03-31 20:21 /dev/sdb
```

is it detected or not?
how to mount it?

i did some research. there are the links that i found.
[http://superuser.com/questions/106094/can-not-mount-my-usb-disk-ubuntu-nor-windowsdmesg-including](http://superuser.com/questions/106094/can-not-mount-my-usb-disk-ubuntu-nor-windowsdmesg-including)
[http://www.reactivated.net/writing_udev_rules.html#example-camera](http://www.reactivated.net/writing_udev_rules.html#example-camera)
[http://androidforums.com/samsung-galaxy-s2-international/429162-unable-access-sd-card-linux.html](http://androidforums.com/samsung-galaxy-s2-international/429162-unable-access-sd-card-linux.html)
[http://en.gentoo-wiki.com/wiki/SD_and_MMC_card_readers](http://en.gentoo-wiki.com/wiki/SD_and_MMC_card_readers)
[http://www.gentoo-wiki.info/Multicard_reader](http://www.gentoo-wiki.info/Multicard_reader)

what to do?

---

### Post by azertyh on 2012-04-02
hello,
in this [link]("http://vanilla.slitaz.org/index.php?p=/discussion/1856/solved-sd-card-not-recognized/p1"), the issue is solved by compiling the kernel with ```
CONFIG_SCSI_MULTI_LUN=y
```
how to do that with xubuntu?

---

