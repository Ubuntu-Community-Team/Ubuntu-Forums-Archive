---
title: "LVM problem"
date: 2012-07-17
forum: General Help
---

### Post by julien80 on 2012-07-17
Hello all,
 
Since I've rebooted my ubuntu 10.04 lts it seems that my LVM is corrupted and I can't start my server anymore...
I need to recover some files on it so it will be great if someone have a solution :)
 
here is my device list and my pvscan :
 
[http://www.hostingpics.net/viewer.php?id=618831pvscan.jpg](http://www.hostingpics.net/viewer.php?id=618831pvscan.jpg)
 
One of the PV is unknown and it's /dev/sda5 I surely think...
 
Please help me :(

---

### Post by julien80 on 2012-07-17
I'm working on it and pass a step :)
 
I've recreated the pv with the missing uuid with 'pvcreate --uuid .... /dev/sda5'
 
Now my LV are well known :
 
#lvscan
Ignoring additional label on /dev/sda5 at sector 2
ACTIVE               '/dev/tellus/root'  [49.30 Gib] inherit
ACTIVE               '/dev/tellus/swap_1'  [388.00 Mib] inherit
 
But when I try to mount root :
 
#mount /dev/tellus/root /mnt
mount: you must sprecify the filesystem type
 
I have tried some filesystem but it seems that nothing works.... 
 
What can I try ??
 
Thank you for your answer 
 
Julien

---

### Post by steeldriver on 2012-07-17
Hi Julien - a couple of suggestions:

For the fstype can you look at your original /etc/fstab file? If not, you can try either of the following:

```
# parted /dev/tellus/root print
``````
# file -sL /dev/tellus/root
```To mount the volume, you *may* find that the 'mount' command won't work with the /dev/tellus/root symlink, iirc I had to use the symlinks under /dev/mapper which should be something like

```
/dev/mapper/*vgname-lvname*
```i.e.
```
/dev/mapper/tellus-root
```If/when you make a permanent entry in your fstab you should probably replace those with the equivalent UUIDs

---

### Post by julien80 on 2012-07-17
Hello Steeldriver,
 
Thanks for your quick answer !
 
when I try to mount with /dev/mapper/tellus-root, I have the same result.
 
and with :
 
#parted /dev/tellus/root print
Error: /dev/dm-0: unrecognised disk label
 
#file -sL /dev/tellus/root 
/dev/tellus/root: data
 
Doesn't sounds really good..?!

---

### Post by steeldriver on 2012-07-17
did you check your original /etc/fstab file? that should include the fstype info that the volume was originally mounted with

I have only played with lvm2 on 11.10, it may be different on 10.04 in particular you might need to load an additional kernel module first... ?

```
# modprobe dm-mod
```

---

### Post by julien80 on 2012-07-17
In fact I'm booting on a ubuntu livecd ... so I can't check the original /etc/fstab file ... 
 
Sure, I've read somewhere about 
 
# modprobe dm-mod
 
but it's not the problem here I think I don't know why the system don't mount automatically the volume and ask for filesystem type....
Maybe I need to specify something on the VG or LV since I've reassign the UUID to one of the PV ?

---

### Post by steeldriver on 2012-07-17
my bad - I was forgetting the original /etc/fstab is probably on the volume you're trying to mount

fwiw this poster is having a similar issue - I wish I knew how to fix it - sorry

[http://ubuntuforums.org/showthread.php?t=2026362](http://ubuntuforums.org/showthread.php?t=2026362)

---

### Post by julien80 on 2012-07-17
No problem , thank you for answering me :) cause there is not really crowd to answer to my troubles!
 
Here is a screenshot of my partitions in Gparted as a clue :
 
[http://www.hostingpics.net/viewer.php?id=840733gparted.jpg](http://www.hostingpics.net/viewer.php?id=840733gparted.jpg)
 
Hope someone has an idea :)

---

### Post by julien80 on 2012-07-18
Hello,
 
When I do 
 
#fdisk -l
...
Disk /dev/mapper/tellus-root doesn't contain a valid partition table
 
Is there any way to repair this partition table?

---

### Post by steeldriver on 2012-07-18
> **julien80 said:**
> Hello,
 
When I do 
 
#fdisk -l
...
Disk /dev/mapper/tellus-root doesn't contain a valid partition table
 
Is there any way to repair this partition table?

Ignore that - it's normal, afaik fdisk can't read inside lvm volumes - mine says the same.

EDIT: I just looked at the pic from your previous post and noticed that gparted says "point de montage : tellus" - are you sure the volume is not already mounted? what do you get if you just type 'mount' (with no devices / options) to list all the currently mounted devices?

---

### Post by julien80 on 2012-07-19
Hey, 
 
here is the screenshot but I'm not sure the volume is mounted...
 
[http://www.hostingpics.net/viewer.php?id=410096mountgparted.jpg](http://www.hostingpics.net/viewer.php?id=410096mountgparted.jpg)

---

