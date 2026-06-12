---
title: "Copying a Partition"
date: 2009-12-12
forum: General Help
---

### Post by Narusegawa on 2009-12-12
I've just put in a new 500gb drive to my PC and want to copy an entire 110gb NTFS partition from a different drive to it.

Basically I got /dev/sda3 sitting at the far right of my /dev/sda drive. I'd like to move this over to my new /dev/sdc drive, but ONLY this partition not the others.

GParted won't let me do this in 9.10 as it "cannot read contents of the filesystem". Any other way I can do this?

---

### Post by Leppie on 2009-12-12
very strange that gparted cannot access the volume.
i believe the latest ntfs module (ntfs-3g) is installed in karmic, or is this partition encrypted?

otherwise there's tools like pqmagic which allow you to make a disk image and restore to a different location.

---

### Post by Narusegawa on 2009-12-12
It's not encrypted at all. I can mount in and read through it if I wanted to. Infact I'm playing mp3's from a different partition on another drive that was formatted the same way.

The only special thing about /dev/sda3 which won't copy is that it's inside a logical/extended partition.

Is there an output I can give you to assist in helping me? :)


Edit: I think maybe it needs ntfsprogs which isn't installed by default. I'm assuming this based on the attached screenie from GParted.

---

### Post by coffeecat on 2009-12-12
> **Narusegawa said:**
> 
GParted won't let me do this in 9.10 as it "cannot read contents of the filesystem". Any other way I can do this?

You may need to install the package 'ntfsprogs' before Gparted can do this. A common source of confusion this - ntfsprogs is included in the live CD, hence Gparted on the live CD can deal with NTFS partitions, but not in a default install. Hence you have to install ntfsprogs separately.

But why do you want to use Gparted to copy the contents of a partition? If it's just the folders and files, why not do a drag and drop with Nautilus?

---

### Post by Narusegawa on 2009-12-12
I just realized that myself and edited my own post :)

I was just going to use GParted as I want to maintain all the nt permissions on it etc and everything. Plus the new drive has no partition table yet either. Figured it'd just be easier to copy the partition with GParted and then extend it from 110gb to 250gb all in one go. Without having to make partitions and then copy folders/files.

---

### Post by Leppie on 2009-12-12
so, all is working now?

---

### Post by Narusegawa on 2009-12-12
Yup, just installed ntfsprogs. Reload GParted and did a copy paste from /dev/sda3 into /dev/sdc and it's sitting in a nice window doing an ```
ntfsclone -f --overwrite /dev/sdc1 /dev/sda3
```

Dunno how long it'll take but atleast I can still use my system!

Thanks

---

### Post by Narusegawa on 2009-12-12
ntfsclone has finished (it's not in my TOP) report anymore.

gpartedbin is at 100% with a status of "sleeping" and the main gparted GUI just sitting there... Been like this for 30 mins now... I'm worried it's crashed/hung

---

