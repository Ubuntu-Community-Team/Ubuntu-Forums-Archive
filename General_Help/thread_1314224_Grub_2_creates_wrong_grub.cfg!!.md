---
title: "Grub 2 creates wrong grub.cfg!!"
date: 2009-11-04
forum: General Help
---

### Post by Attanar on 2009-11-04
Well, I just installed the new 9.10 Ubuntu yesterday and configured everything.

But what was my surprise when I restarted to launch my Windows XP partition and I recieved an error telling me about some Windows missing files...

I made some research and found that** GRUB was trying to launch Windows from sda2, while it's actually installed on sda1!!!!!**

Then I thought, well, this can be easily fixed, all I need is to change "menu.lst" file so that it will point to sda1 instead, and everything will work fine again....... but OH SURPRISE! Grub 2 no longer uses menu.lst, but a series of configuration files instead.

The problem is **the configuration I need to change is at file grub.cfg, which is read only (and even if you modify it, grub will rewrite it again), so I can't set grub to launch Windows from sda1.**

Any idea on how to fix this mess?

---

### Post by VMC on 2009-11-04
> **Attanar said:**
> Well, I just installed the new 9.10 Ubuntu yesterday and configured everything.

But what was my surprise when I restarted to launch my Windows XP partition and I recieved an error telling me about some Windows missing files...

I made some research and found that** GRUB was trying to launch Windows from sda2, while it's actually installed on sda1!!!!!**

Then I thought, well, this can be easily fixed, all I need is to change "menu.lst" file so that it will point to sda1 instead, and everything will work fine again....... but OH SURPRISE! Grub 2 no longer uses menu.lst, but a series of configuration files instead.

The problem is **the configuration I need to change is at file grub.cfg, which is read only (and even if you modify it, grub will rewrite it again), so I can't set grub to launch Windows from sda1.**

Any idea on how to fix this mess?

Look at my signature for Grub2 Introduction by ranch hand. Lots of useful information in there with plenty of links.

In the mean time you can edit '/etc/grub.d/40_custom' to suite your needs.

Example:
```
[#!/bin/sh
exec tail -n +3 $0
# This file is an example on how to add custom entries
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e2444e41444e1925
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Fedora release 11 (Leonidas) (on /dev/sda8)" {
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 5dbd9c5c-b1de-489a-a3da-6c3d7fe3ddd3
	linux /boot/vmlinuz-2.6.29.4-167.fc11.i586 root=/dev/sda8
}
```

---

### Post by phillw on 2009-11-04
> **VMC said:**
> Look at my signature for Grub2 Introduction by ranch hand. Lots of useful information in there with plenty of links.

In the mean time you can edit '/etc/grub.d/40_custom' to suite your needs.

Example:
```
[#!/bin/sh
exec tail -n +3 $0
# This file is an example on how to add custom entries
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e2444e41444e1925
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Fedora release 11 (Leonidas) (on /dev/sda8)" {
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 5dbd9c5c-b1de-489a-a3da-6c3d7fe3ddd3
    linux /boot/vmlinuz-2.6.29.4-167.fc11.i586 root=/dev/sda8
}
```

Hi VMC, thanks for the links. I've added them into my list of resources - I'm still waiting to update my Grub2 :p

---

### Post by minosi on 2009-12-05
> **VMC said:**
> Look at my signature for Grub2 Introduction by ranch hand. Lots of useful information in there with plenty of links.
Thanks too, great info there.

Now, I would like to know which IDIOT came up with that brilliant idea of making Boot loader configuration dependent on Operating System ???
I smell Microsoft marketing guy behind this.

Result for me:
1) Grub(2) is now USELESS for anything other than single-OS install of Linux.
2) I lost half a day fighting this auto-corrupting, sorry, auto-updating, stupidity to get Karmic to boot (and survive a reboot) ...

OK. So we are back to Extlinux.

I am surprised that such a major project like Ubuntu reverts to a bootloader generating more trouble than Windows Me one. Makes me sad.

---

