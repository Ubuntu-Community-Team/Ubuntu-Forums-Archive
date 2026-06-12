---
title: "Resizing Partitions"
date: 2009-10-29
forum: General Help
---

### Post by Gonchos on 2009-10-29
I know this has already been asked and answered, but I'd really appreciate some more help while working with gparted. This is what I do:

I boot from life CD, run gparted, and see my 3 partitons :
1. Win XP recovery partition
2. Win 7 partition
3. Ubuntu partition

Now I want to increase Ubunu's storage space while shrinking Win7 and delete win XP if it's possible, but with gparted I can only shrink partitions while leaving a grey "unused space" behind. 

What am I doing wrong?

---

### Post by flipper9 on 2009-10-29
The partition might be "nested" inside of an extended partition (a container of sorts).  You might also need to resize the extended partition that contains the one you are reducing.

---

### Post by drs305 on 2009-10-29
See if this guide on expanding an Ubuntu system partition helps you out:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

It was written for installs that ended up being only 2.5GB, but the principles still apply.

---

### Post by Gonchos on 2009-10-30
Thank you! that link was really helpful

It's working right now, looks like it will take a while

:p Thanks!

---

### Post by Gonchos on 2009-10-30
Everything ran smoothly but now GRUB's menu shows old partitions instead of just the two new ones that showed in gparted.

Do I have to tweak GRUB now?

---

### Post by drs305 on 2009-10-30
> **Gonchos said:**
> Everything ran smoothly but now GRUB's menu shows old partitions instead of just the two new ones that showed in gparted.

Do I have to tweak GRUB now?

Probably. You are using Grub (legacy) and not grub 2?

Post these results:
```

sudo blkid -c /dev/null
sudo fdisk -l  # Lowercase L
cat /boot/grub/menu.lst

```

---

### Post by Gonchos on 2009-10-30
> sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="D2488E03488DE717" TYPE="ntfs" 
/dev/sda5: UUID="b48ddcd7-7761-4495-9f21-fc3684818d44" TYPE="ext4" 
/dev/sda6: UUID="3113a534-652b-4004-9462-ca1f0cff1b20" TYPE="swap"

> sudo fdisk -lDisk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a7b3fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        4565    36668331    7  HPFS/NTFS
/dev/sda3            4566        9729    41479830    5  Extended
/dev/sda5            4566        9678    41070141   83  Linux
/dev/sda6            9679        9729      409626   82  Linux swap / Solaris

> cat /boot/grub/menu.lstcat: /boot/grub/menu.lst: No such file or directory

EDIT: I tried to reinstall grub (by the way it's grub2) with no success I guess

---

### Post by drs305 on 2009-10-30
> **Gonchos said:**
> 
EDIT: I tried to reinstall grub (by the way it's grub2) with no success I guess

Grub 2 is a totally different animal.

Are you able to boot into your system and just want to eliminate older partitions or are you having trouble booting into the system at all?

If the latter (having problems getting into your system), take a look at the community doc GRUB 2 page. There is a section on how to boot the system from either the 1) menu or 2) the grub or grub-rescue prompt. The link is the first one in my signature line (GRUB2). There is also a section on returning to Grub legacy, but I'd recommend sticking with G2.

If the former, run "sudo update-grub" and see if things get updated and corrected.

---

### Post by Gonchos on 2009-10-30
I couldn't boot into my system, and I've already reinstalled grub, but now when I boot, i see my old partitions menu and none of those options work.

I'm back on square 1

---

