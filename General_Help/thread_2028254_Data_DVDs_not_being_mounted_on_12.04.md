---
title: "Data DVDs not being mounted on 12.04"
date: 2012-07-17
forum: General Help
---

### Post by TheGostak on 2012-07-17
Im trying to reinstall everything after a harddrive died. I had been using an upgraded ubuntu 12.04 with xubuntu-desktop installed, the same dvds worked at that time. With the new hard drive I installed ubuntu 12.04 from the live cd but it seems the dvd drive wont recognise my backup dvds, it mounts audio cds and dvd films fine though.  hwinfo -- cdrom ```
 24: SCSI 100.0: 10602 CD-ROM (DVD)                                 [Created at block.247]   UDI: /org/freedesktop/Hal/devices/storage_serial_HL_DT_STDVD___RW_GT32N_KZ2A8385256   Unique ID: KD9E.JxKNuu7TQtF   Parent ID: w7Y8.jA0tpkGgPlD   SysFS ID: /class/block/sr0   SysFS BusID: 1:0:0:0   SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0   Hardware Class: cdrom   Model: &quot;HL-DT-ST DVD+-RW GT32N&quot;   Vendor: &quot;HL-DT-ST&quot;   Device: &quot;DVD+-RW GT32N&quot;   Revision: &quot;A102&quot;   Driver: &quot;ahci&quot;, &quot;sr&quot;   Driver Modules: &quot;ahci&quot;   Device File: /dev/sr0 (/dev/sg1)   Device Files: /dev/sr0, /dev/cdrom, /dev/cdrw, /dev/disk/by-id/ata-HL-DT-STDVD+_-RW_GT32N_KZ2A8385256, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0, /dev/dvd, /dev/dvdrw   Device Number: block 11:0 (char 21:1)   Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM   Drive status: no medium   Config Status: cfg=new, avail=yes, need=no, active=unknown   Attached to: #12 (SATA controller)   Drive Speed: 24 
```  mount -t iso9660 /dev/sr0 /media/cdrom ```
mount: no medium found on /dev/sr0
```  anyone got any ideas?

---

### Post by The Linuxist on 2012-07-17
You could try dumping the data to an ISO and mounting that?

```
dd if=/dev/sr0 of=backupDVD.iso bs=2048 conv=noerror,sync
```

then mouting it:

```
mount -t iso9660 -o loop backupDVD.iso /media/cdrom
```

---

### Post by TheGostak on 2012-07-19
The same error as before:

dd: opening `/dev/sr0': No medium found

---

### Post by ccoupe on 2012-08-18
I have the same problem with Ubuntu 11.10. Works fine with DVD-Videos but won't mount backup DVD's created by (probably 11.04). It doesn't believe there is media in the drive but it does try many times to spin it up. The dvd's were written on the same drive and cpu and they mounted back in the 11.04 days, about the same time, I created burned the DVD-Video that does mount. It's not the drive. This is a software problem.

One other data point. I was able to mount a DVD-Data once, I think, but never again. Too weird! It's almost like there is a persisent cache of previously mounted DVDs info and some bug in 11.10 (and reportedly 12.04) says the DATA-DVDs created is not correct. 

Could it be I'm running GNOME shell instead of Unity? Seems like a wacky thought. ~/. is a cache. I'll have to log out and into unity to find out. Ick.

Time passes..

I tried Unity. Doesn't mount back up DVDs. I upgraded to 12.04. Doesn't mount backup DVD's.

---

