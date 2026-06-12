---
title: "Universal Storage Adapter drivers"
date: 2010-02-03
forum: General Help
---

### Post by altjx on 2010-02-03
I have a NexStar Universal Storage Adapter that I purchased awhile ago when I had linux. I have it hooked up to a 3.5" hard drive and trying to format it, but when I turn the hard drive on, nothing comes up in Linux like it did (as an external drive in Windows).

[http://www.vantecusa.com/front/product/view_detail/393](http://www.vantecusa.com/front/product/view_detail/393) is a better view of the image

When I go to terminal, and type lsusb, it's at least recognizing it. 
This is what it shows when I type lsusb

Bus 002 Device 006: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

But nothing comes up. Anyone know how to get it working?
I've called and spoke with the guys there but they said they don't support linux

Nevermind, I got it working. Anyone who has this issue, the way I resolved it was to disconnect the USB cable, turn ON the power adapter, and then connect the USB cable. It'll read it exactly as an external hard drive it appears

---

### Post by audiomick on 2010-02-03
What do you get from
```
sudo fdisk -l
```
the last character is a lower case L, not a figure one.

---

### Post by altjx on 2010-02-03
sudo fdisk -l gives me this

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x086f8f0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37609   302094261   83  Linux
/dev/sda2           37610       38913    10474380    5  Extended
/dev/sda5           37610       38913    10474348+  82  Linux swap / Solaris

Disk /dev/sdh: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0dd407d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       10336    78140128+   7  HPFS/NTFS


How do I format my external HD? it's 80GB
I've tried sudo mkfs.vfat /dev/sdh1 and i get this
mkfs.vfat 3.0.3 (18 May 2009)
mkfs.vfat: /dev/sdh1 contains a mounted file system.

---

### Post by audiomick on 2010-02-03
The computer can see it

```
Disk /dev/sdh: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0dd407d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       10336    78140128+   7  HPFS/NTFS

```That it is there, I am sure.

It has an NTFS partition on it occupying the whole drive.

Can you see it at
places> computer?

---

### Post by altjx on 2010-02-03
> **audiomick said:**
> The computer can see it

```
Disk /dev/sdh: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0dd407d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       10336    78140128+   7  HPFS/NTFS

```That it is there, I am sure.

It has an NTFS partition on it occupying the whole drive.

Can you see it at
places> computer?

Yeah, sorry, I edited my first post showing that I was able to get it resolved. I just went ahead and downloaded Gparted to go ahead and format the partition. Thanks guys :)

---

### Post by audiomick on 2010-02-03
Put a "solved" tag on the thread. That is available under "thread tools" at the top of the thread.

---

