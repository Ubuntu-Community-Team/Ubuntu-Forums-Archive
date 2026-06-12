---
title: "Kernel does not recognize USB"
date: 2009-12-19
forum: General Help
---

### Post by renoy29985 on 2009-12-19
Hi Experts,

My kernel does not recognize a USB inserted, as I am not able to find a devices file in /proc/bus/usb. But strangely I am able to view and mount the USB mounted in GUI.

I basically connected a Reliance Netconnect Broadband USB.

Please help.

Many thanks,
Renoy.

---

### Post by Sin@Sin-Sacrifice on 2009-12-19
What's the output of ```
sudo fdisk -l
```

---

### Post by renoy29985 on 2009-12-20
Hi,

Below is the output of "sudo fdisk -l" :

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe99ce99c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6844    54974398+   7  HPFS/NTFS
/dev/sda2            6845       29775   184193257+   f  W95 Ext'd (LBA)
/dev/sda3           29776       38913    73400985   83  Linux
/dev/sda5            6845       27376   164923258+   7  HPFS/NTFS
/dev/sda6           27377       29726    18876343+  83  Linux
/dev/sda7           29727       29775      393561   82  Linux swap / Solaris

Many thanks,
Renoy.

---

### Post by 3rdalbum on 2009-12-20
Go to the Network Manager applet, right-click on it and choose Edit Connections.

Click the Mobile Broadband tab and click the Add button. Input the information for your broadband provider. See if this works.

The /proc/bus/usb/devices mustn't be any anything to worry about, it's not present on my system either.

---

### Post by renoy29985 on 2009-12-20
> **3rdalbum said:**
> Go to the Network Manager applet, right-click on it and choose Edit Connections.

Click the Mobile Broadband tab and click the Add button. Input the information for your broadband provider. See if this works.

The /proc/bus/usb/devices mustn't be any anything to worry about, it's not present on my system either.

Thanks a lot. This worked. Seemed to have completely made a micky of myself :). Apologies for such silly queries.

---

