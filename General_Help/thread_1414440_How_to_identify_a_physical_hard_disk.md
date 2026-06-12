---
title: "How to identify a physical hard disk"
date: 2010-02-23
forum: General Help
---

### Post by lemurid on 2010-02-23
I have a 4 disk software RAID array made up of Seagate drives. Let's name them sda, sdb, sdc, sdd. And let's say SDC is failing. Big question. How do i find out which of the 4 physical drives it is? They all look the same to me when i open up the PC case. Maybe some utility which will load up heavy usage on just one drive and i will try to put my finger on them and figure out which one is vibrating? Or maybe there is a smarter way?

---

### Post by ajgreeny on 2010-02-23
Run ```
sudo lshw -C disk
``` to show output like this

> *-disk:0                
       description: ATA Disk
       product: Maxtor 6B160P0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       **logical name: /dev/sda**
       version: BAH4
       **serial: B40R83YH**
       size: 152GiB (163GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d44cd44c
You should find the serial number on a label on each disk.

---

