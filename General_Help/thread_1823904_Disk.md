---
title: "Disk"
date: 2011-08-12
forum: General Help
---

### Post by nconceicao on 2011-08-12
Hello,

I am fairly new to ubuntu and have been learning linux using this distro. I am using Ubuntu 11.04 server.

Recently I added a new HD to the desktop.. however I know I need to mount it,

My question is how would I mount this disk? so I can use it as a drive?

Thanks

---

### Post by nconceicao on 2011-08-12
here are my disks, I want to mount and use constantly the 400GB

Here is what i see now

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             7.4G  7.0G   35M 100% /
none                   99M  220K   99M   1% /dev
none                  106M     0  106M   0% /dev/shm
none                  106M  436K  106M   1% /var/run
none                  106M     0  106M   0% /var/lock

  *-disk:0
       description: ATA Disk
       product: ST3400620A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 3QH0204J
       size: 372GiB (400GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000cd8fa
  *-disk:1
       description: ATA Disk
       product: FUJITSU MPE3084A
       vendor: Fujitsu
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: EE-C
       serial: 05097126
       size: 8063MiB (8455MB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00062819
  *-cdrom
       description: DVD writer
       product: DVDRW SHW-16H5S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: LS0N
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc

---

### Post by oldos2er on 2011-08-13
You'll need to partition, then format before you can mount the disk. Once you've done that, edit your /etc/fstab file to have it mounted on bootup.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Furball588 on 2011-08-13
The results of an sudo fdisk -l may be easier to read here.  

Just my initial reaction, it may be easiest to just load gparted and just partition, format and set a mount point in there.

---

