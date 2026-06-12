---
title: "usb device not registering"
date: 2012-08-22
forum: General Help
---

### Post by settoloki on 2012-08-22
Hi I am a beginner ubuntu user and I am having problems with a usb device, I tried it on windows and all though it registered it did not show under my computer and if I tried to format it it asked me to insert device into drive.

I did some googling and it seems ubuntu might be the answer to repairing it.

anyway I plugged it into my ubuntu box and opened up the syslog this is the output

```

Aug 22 22:50:06 ubuntu kernel: [ 1156.138389] usb 2-1.2: new high-speed USB device number 6 using ehci_hcd
Aug 22 22:50:07 ubuntu kernel: [ 1156.233269] scsi7 : usb-storage 2-1.2:1.0
Aug 22 22:50:07 ubuntu mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Aug 22 22:50:07 ubuntu mtp-probe: bus: 2, device: 6 was not an MTP device
Aug 22 22:50:08 ubuntu kernel: [ 1157.229050] scsi 7:0:0:0: Direct-Access     Innostor NAND Flash       1.00 PQ: 0 ANSI: 5
Aug 22 22:50:08 ubuntu kernel: [ 1157.230723] sd 7:0:0:0: Attached scsi generic sg2 type 0
Aug 22 22:50:08 ubuntu kernel: [ 1157.233941] sd 7:0:0:0: [sdb] Attached SCSI removable disk


```it is my understanding I am suppose to be able to see some sort of drive name /dev/sdx but I don't and I have to admit I'm not sure what the rest means, is there anybody out there that could offer me some help in getting this flash drive to register on ubuntu or windows

---

### Post by matt_symes on 2012-08-23
Hi

Is the device partitioned ?

Open a terminal and type

```
ls -l /dev/sdb
```That is a small L after ls. Post the results back here.

Is the device a USB 3.0 device ?

Kind regards

---

### Post by SlugSlug on 2012-08-23
You could install gparted - that makes it easy for partitioning / formatting drives

```
sudo apt-get install gparted
```

---

### Post by mzaam on 2012-08-23
testdisk also worth to try, it is powerfull for recovering disk

```
 sudo apt-get install testdisk
```

---

