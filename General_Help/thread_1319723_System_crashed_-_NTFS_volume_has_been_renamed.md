---
title: "System crashed - NTFS volume has been renamed"
date: 2009-11-08
forum: General Help
---

### Post by keef_ca on 2009-11-08
I'm using Ubuntu 9.10 (Karmic Koala). Everything after the upgrade was fine. A few hours later the power flickered and the PC went down hard. When it came backup an NTFS partition is no longer correctly named "disk". It now is labeled the same as the UUID.

 It should be

 /dev/sda3/media/disk

 and its it now

/dev/sda3/media/479BFA167C5A23AE

 I tried to correct the name using GParted and Disk Utility but neither worked. I'm not saying the upgrade process or the new code itself is in any way to blame. It was the power outage.

Any help is appreciated. Just an FYI - my Linux experience it minimal at best. Please take that into consideration with any answer.

                            thanks everyone

---

### Post by coffeecat on 2009-11-08
To be able to label NTFS partitions in Gparted, Disk Utility or in the terminal, you need the package 'ntfsprogs' installed. Go to Synaptic and install ntsfprogs. But having said that, you've had an inexplicable change to a NTFS filesystem following an unclean shutdown. I would be wary of doing anything more with it in Linux until I've done a chkdsk in Windows. Do you have a Windows installation on that machine? If so, you might be wise to boot into Windows first and do a chkdsk. And then you can change the partition label quite easily using Windows.

I'm a bit puzzled by exactly what you mean by:

> **keef_ca said:**
> 
 /dev/sda3/media/disk

 and its it now

/dev/sda3/media/479BFA167C5A23AE


Your mount point is/was /media/disk (I guess) and your Ubuntu root partition is sda3 (I guess), but you don't normally refer to /media/disk as /dev/sda3/media/disk when you are working from an installation on /dev/sda3. Or perhaps you meant something else. Why not post the terminal output of these two commands?

```
sudo blkid
sudo fdisk -l
```Then we'll have a clearer idea of your partition layout and partition labels.

---

