---
title: "Recognize - mount ext drive on USB to SATA+PATA ADAPTER"
date: 2011-09-30
forum: General Help
---

### Post by parovelb on 2011-09-30
I would like to transfer data from my notebook's HD to my desktop. The notebook HD does not mount. 

I have a WD800 drive attached to STLab USB to PATA + SATA adapter. 

Below is my otput.

```
:/$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bajtov
255 heads, 63 sectors/track, 19457 cylinders
Units = steze of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a76f9

Naprava   Zagon    Za&#269;etek       Konec     Bloki    Id  Sistem
/dev/sda1   *           1       19272   154798080   83  Linux
/dev/sda2           19272       19458     1489921    5  Razširjen
/dev/sda5           19272       19458     1489920   82  Linux izmenjalni / Solaris

:/$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Loading the driver with ```
sudo modprobe pata_jmicron.ko
``` does no difference.

How can I get to my data on the disk? Any ideas?

---

