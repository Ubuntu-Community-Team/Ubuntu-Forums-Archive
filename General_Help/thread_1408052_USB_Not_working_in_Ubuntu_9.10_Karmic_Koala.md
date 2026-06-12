---
title: "USB Not working in Ubuntu 9.10 Karmic Koala"
date: 2010-02-15
forum: General Help
---

### Post by neuflex on 2010-02-15
Hello All,

I am having a few problems connecting USB devices in Ubuntu 9.10 Karmic Koala (Ipod, Flash Stick and Canon Camera). A USB mouse works with no problems.

the log file displays this every time I connect a device, with the address changing: -

```

using ehci_hcd and address 87
Feb 15 19:47:18 tomsk kernel: [ 1796.520163] usb 1-4: new high speed USB device using ehci_hcd and address 112
Feb 15 19:49:03 tomsk kernel: [ 1902.172081] usb 1-4: new high speed USB device using ehci_hcd and address 4
Feb 15 19:49:06 tomsk kernel: [ 1904.364058] usb 1-4: new high speed USB device using ehci_hcd and address 15
Feb 15 19:49:06 tomsk kernel: [ 1904.676083] usb 1-4: new high speed USB device using ehci_hcd and address 16
Feb 15 19:49:11 tomsk kernel: [ 1909.696076] usb 1-4: new high speed USB device using ehci_hcd and address 42
Feb 15 19:49:12 tomsk kernel: [ 1911.240181] usb 1-4: new high speed USB device using ehci_hcd and address 49

```

I have tried looking for a thread with the same problem but I can't find anything.

Any help would be much appreciated.

Thanks in Advance

---

### Post by ironclaw on 2010-02-16
What does
```
sudo fdisk -l
```
show when a USB device is connected?

---

### Post by neuflex on 2010-02-16
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00088ec2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris


```

Thanks for your help

---

### Post by YaKillaCJ on 2010-02-18
Yea im havin the same issue. Ive been tryin 2 connect my iPod Touch first generation or iPod Nano (idk what ver).
On iPod Touch, most I get is to see the photos on it like its a camera.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe02f6114

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       14653   117596160    7  HPFS/NTFS
/dev/sda3           14654       24007    75136005    5  Extended
/dev/sda4           24008       30401    51359805    7  HPFS/NTFS
/dev/sda5           14654       23577    71681998+  83  Linux
/dev/sda6           23578       24007     3453943+  82  Linux swap / Solaris

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         984     1983619+   6  FAT16

```

---

### Post by slatfatf on 2010-02-19
I'm having same trouble here, although the reason can be different.

The actual problems began here when I got (finally) my iphone sync with ifuse working. 
Before my automount and fdisk found my camera just fine, but afterwards I haven't found any good reason why my camera is not found (actually before my iphone was also "autodetected", but it doesn't happen either anymore). It must be something with the libs installed when I got iphone working...

External HD automounts nicely, but camera not.

---

### Post by strumusa on 2010-03-01
> **neuflex said:**
> ```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00088ec2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris


```Thanks for your help
   
I've got the exact same deal...Can't upload my pics from my cell phone lg550 fusic...My fdisk -l output shows the following:  

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1e6e1e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris
    
But what does any of this tell me?  Please help us newbies...thanks

---

### Post by ellgor on 2010-03-01
Hi,

Check with synaptic to see if you have "usbmount", it might solve your problem.

Regards, Ellgor.

---

### Post by astarmathsandphysics on 2010-04-23
Nope.

It still works in 8.04

---

