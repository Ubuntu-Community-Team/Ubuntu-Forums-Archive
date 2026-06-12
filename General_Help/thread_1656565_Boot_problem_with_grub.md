---
title: "Boot problem with grub"
date: 2010-12-31
forum: General Help
---

### Post by sidox.me on 2010-12-31
I had to return a laptop with only window xp os on it, so i deleted the ubuntu partition from the windows disk manager. Now when i restart my computer it shows, error: no such partition grub rescue> comes up. i have tried loading a windows xp instalation cd to fix mdr, but it doest load/boot at all. what should i do? Im new to ubuntu. NEED HELP! URGENT!!! also i cant operate windows xp at all, so suggest like wise.......

---

### Post by lisati on 2010-12-31
> **sidox.me said:**
> I had to return a laptop with only window xp os on it, so i deleted the ubuntu partition from the windows disk manager. Now when i restart my computer it shows, error: no such partition grub rescue> comes up. i have tried loading a windows xp instalation cd to fix mdr, but it doest load/boot at all. what should i do? Im new to ubuntu. NEED HELP! URGENT!!! also i cant operate windows xp at all, so suggest like wise.......

It has been a while since I've done this, so others might be able to elaborate and/or correct the procedure I'm suggesting. You might also want to consider booting from a Live CD and backing up your important data first, just in case something goes haywire.

A useful tool at this stage would be a Windows installtion disk. If it's one came with your laptop or one you've purchased, and it's not an OEM recovery disk, you should be sweet. Boot from the disk, select the "Repair" option, and you should be able to get XP bootable again.

Good luck!


Edit: the above assumes that there's already an XP partition there, and won't work if it isn't.

---

### Post by Nytram on 2010-12-31
Are you saying the win xp installation cd wont boot? Youll need to enter bios and select the cd drive as the first boot option.

---

### Post by Hur Dur on 2010-12-31
You're in the grub command-line, right? Try using the following command:

```

menuentry "Windows" {
set root=(hd0,1)
chainloader +1
}

```

The set root line should be changed to whatever partition Windows is on. If it's /dev/sda1, it should be set root=(hd0,1) if it's /dev/sda2, it should be set root=(hd0,2) and so on. This of course, is assuming that Windows is installed correctly, and GRUB is installed correctly.

---

