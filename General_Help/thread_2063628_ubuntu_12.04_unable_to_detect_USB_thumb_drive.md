---
title: "ubuntu 12.04 unable to detect USB thumb drive"
date: 2012-09-27
forum: General Help
---

### Post by avee137 on 2012-09-27
Hi,

When i insert thumb drive to USB. I get kernel message like :```
[ 2578.256128] usb 2-3: new high-speed USB device number 4 using ehci_hcd
[ 2776.508132] usb 2-1: new high-speed USB device number 5 using ehci_hcd

```

which suggests it is connected successfully however it is not mounted to /media or any other mount point. i don't see it even when i do a 'fdisk -l' or run 'gparted'

when i do 'lsusb' i get following output:
```
Bus 002 Device 004: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 002 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick

```


Please suggest what could be possible solution for this issue.

Thanks in advance.

---

