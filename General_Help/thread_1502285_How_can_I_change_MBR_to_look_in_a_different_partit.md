---
title: "How can I change MBR to look in a different partition for /boot/grub?"
date: 2010-06-05
forum: General Help
---

### Post by raysa on 2010-06-05
I have two versions of Ubuntu 10.04 on my computer - the desktop version (which I want) and the Netbook version (which I installed to get me out of a previous booting prob but I no longer want, and which I wish to remove to free up hdd space to tidy up partition allocations).

But the computer boots up from the /boot/grub in the unwanted partition rather than the /boot/grub in the wanted installation. They have different menus and are easily distinguished.  

boot_info_script confirms the situation with: "=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in partition #8 for /boot/grub." (#8 is the partition with the unwanted installation, whereas I want it to use the one in #6).

The BIOS (Phoenix) initial display doesn't give any options for telling MBR to target the wanted grub.  How can I change the MBR to forget the 'wrong' grub and point to the desire one?

Thanks, Ray

---

### Post by Leppie on 2010-06-05
boot into the system you want grub2 to use for its configuration files.
then issue the following command:
```
sudo grub-install --recheck /dev/sda
```

---

### Post by raysa on 2010-06-05
You're a star, Leppie. Worked a treat. Many thanks.

One more question, though ...

It now boots up the system I want from within itself, so I have deleted the unwanted partitions (unwanted installation plus associated swap file), and would now like to allocate the freed space to the active system.

The partition application I have, GParted, won't let you re-size a partition that is currently active. I have a very seldom-used Windows XP partition so I suppose I could boot into that and do it from there?  Do you (or anyone else reading) know of a Windows partitioning app that'll do the trick?  Or is there a neater way?

Thanks again, Ray

---

### Post by Leppie on 2010-06-05
i'd say the best/easiest way to go about doing this is to format the freed up spaces and create mount points for them (or just one of the space is contiguous).
if you do not like that, you could always make a backup of the system and boot off a livecd and expand the partitions (gparted is included in the livecd's)

---

### Post by dino99 on 2010-06-05
yeah, never use a formatting tool on active hdd

boot on a nice tool: [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by efflandt on 2010-06-05
An alternative would be to boot an install CD to a live system and use gparted on that to create, resize any partitions.

---

### Post by raysa on 2010-06-06
Many thanks all. My computer is just as I want it now.

Partedmagic is indeed a great tool, thanks dino99.
The CD should be on everyone's shelf.

Ray

---

