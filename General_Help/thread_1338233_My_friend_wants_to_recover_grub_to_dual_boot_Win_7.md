---
title: "My friend wants to recover grub to dual boot Win 7 and Ubuntu but..."
date: 2009-11-26
forum: General Help
---

### Post by hoppipolla on 2009-11-26
If it turns out that Grub fails to boot 7 and so she is left with only one OS (it is probably best we have 7 or both, but not just Lin at the moment)... what is the best way to recover just 7's  bootloader without risking it wiping Linux or anything like that in the process? Is that easy?

Thanks!

Hoppi :)

---

### Post by t.rei on 2009-11-26
I'm not shure about how it works using grub2 as karmic does, but I expect it to be somewhat the same procedure:

Boot from live-cd, chroot to your system, run the grub setup.

One thing that confused me when installing windows 7 on another partition was that it silently creates two partitions: a small boot partition and the system one. You have to point your windows7 booting in grub to the small one (mine pointed at the wrong one, but I've done it manually and not in grub2...).

So watch out for that. One of the easiest ways to find your actual partitioning is to look at it using gparted from the live-cd.

---

### Post by Skripka on 2009-11-26
Grub boots Win7 fine here, with no extra playing.

Are we talking Grub1 or Grub2?

---

### Post by hoppipolla on 2009-11-26
> **t.rei said:**
> I'm not shure about how it works using grub2 as karmic does, but I expect it to be somewhat the same procedure:

Boot from live-cd, chroot to your system, run the grub setup.

One thing that confused me when installing windows 7 on another partition was that it silently creates two partitions: a small boot partition and the system one. You have to point your windows7 booting in grub to the small one (mine pointed at the wrong one, but I've done it manually and not in grub2...).

So watch out for that. One of the easiest ways to find your actual partitioning is to look at it using gparted from the live-cd.

Oh I see, I actually let GRUB 2 do it itself, but I still couldn't get it working personally ._.  My Windows 7 is on a different disk, her's is on a different partition on the same disk.

> **Skripka said:**
> Grub boots Win7 fine here, with no extra playing.

Are we talking Grub1 or Grub2?

2 :)

---

### Post by Maheriano on 2009-11-26
I'll post it once I find it. Had the same issue last week.

EDIT - [http://ubuntuforums.org/showthread.php?t=1322065](http://ubuntuforums.org/showthread.php?t=1322065), what's your next wish?

[IMG]http://cdn3.ioffer.com/img/1109232000/_i/5796324/1.jpg[/IMG]

---

