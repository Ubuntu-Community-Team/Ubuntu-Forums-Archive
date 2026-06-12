---
title: "Natty 11.04 stop booting"
date: 2011-07-03
forum: General Help
---

### Post by knezmej on 2011-07-03
11.04 natty narwhale (2.6.38-10) stops booting.  It'd done after work with: gparted, palimpsest, mountmanager. 

sda:
  sda1 ntfs flag: boot  Windows 7  mbr 
sda2 ntfs 
sda3 extended flag: lba (?)   
   sda5 ntfs 
     sda6 ext4  Ubuntu 11.04 
sda4 ext4   

It stops after:
  ```
uhci_hcd 0000:00:1d.0: Unlink after no-IRQ? Controller is probably using the wrong IRQ
```another time (after edit in Grub 1.98 with "c" or "e"):
```

Begin: Running /scripts/local-bottom ... done. 
done.
Begin: Running /scripts/init-bottom ... done.

```or
```

usbhid: USB HID core driver 
init: plymouth main process (256) terminated with status 1
init: plymouth-splash main process (885) terminated with status 2

```or
```
ata7: SATA link down (SStatus 0 Scontrol 300) ata8: SATA link down (SStatus 0 Scontrol 300)
```How can I boot it? Thank You.

---

