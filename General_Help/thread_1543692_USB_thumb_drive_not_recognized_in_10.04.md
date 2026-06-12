---
title: "USB thumb drive not recognized in 10.04"
date: 2010-08-01
forum: General Help
---

### Post by sdbrain on 2010-08-01
i tried to connect my samsung usb mp3 player and it is not showing up in mycomp. 
i tried to debug the issue but being a noob i didnt get anywer..:)

this thumb drive does not showup in the fdisk -l output


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       15272   121133313    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           15272       19458    33618945    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           19280       19458     1427456   82  Linux swap / Solaris
/dev/sda6           15272       19109    30819328   83  Linux
/dev/sda7           19109       19280     1368064   82  Linux swap / Solaris




output of dmesg | tail

[69884.424070] usb 1-1: new high speed USB device using ehci_hcd and address 4
[69884.556471] usb 1-1: config 1 interface 0 altsetting 0 endpoint 0x83 has an invalid bInterval 0, changing to 9
[69884.557144] usb 1-1: configuration #1 chosen from 1 choice
[69885.932088] usb 1-1: reset high speed USB device using ehci_hcd and address 4


any help will be greatly appreciated.

---

### Post by TeoBigusGeekus on 2010-08-01
Does it show with
```
lsusb
```
?

---

### Post by bizmeds on 2010-08-01
I am having the same problem as sdbrian I do see the usb devices using the command lsusb however, when trying to boot from the flash drive or the external cd they do not show in the bios nor in the computer menu.

---

