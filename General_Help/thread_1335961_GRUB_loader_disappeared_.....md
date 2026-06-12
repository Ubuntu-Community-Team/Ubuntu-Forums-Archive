---
title: "GRUB loader disappeared ...."
date: 2009-11-24
forum: General Help
---

### Post by ibates on 2009-11-24
I have been booting either Win XP or Ubuntu 9.10 via GRUB for some time.  No problems.  A few minutes ago when finishing up Windows to boot up in the more used Ubuntu, all of a sudden, no GRUB.

No utilities or other software modifications or additions had been made in Windows.  Just a simple Internet access.

Being clever, I selected F8 at the BIOS startup the next time and went straight to the boot device selection menu.  I selected the HDD dedicated to Ubuntu and all I got was a blinking cursor.

It seems Ubuntu has been spirited away into cyberspace.

The Ubuntu HDD shows up as healthy in the Windows Disk manager.

What could have happened?  But much more importantly, what can I do about it?

I would prefer to boot from the BIOS "Select Boot Device" screen rather than by the GRUB loader if that is possible, but at the moment, it looks like, as I said above, Ubuntu is off somewhere in cyberspace.

Should I be able to access the Ubuntu HDD if I boot up on the Live CD?

This is a major problem as all my business data is on the Ubuntu HDD, even though I have backed it up onto yet another disk.  But without Ubuntu, I can't get at it.

---

### Post by namok on 2009-11-24
Download program [Super Grub Disk]("http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso"), burn the disc, start the computer from the cd and select the following options from the menu:
```
1. Choose Language & NO HELP
2. English Super Grub Disk
3. Gnu/Linux
4. Boot Gnu/Linux
5. Boot Gnu/Linux Directly
```Spergrub should "find" Ubuntu.
Then you can easily restore grub to the MBR using the command:
```
sudo grub-install /dev/sdX
```where X is the hard drive letter (a- first, b-second)

---

### Post by JoelOl75 on 2009-11-24
Also make sure your Windows isn't on a "Dynamic" partition and NEVER convert to one, keep it a basic partition.  This will break grub every time Windows boots up.

See [http://www.linuxforums.org/forum/redhat-fedora-linux-help/19499-grub-xp-red-hat-9-fails-after-dynamic-disk-conversion.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/19499-grub-xp-red-hat-9-fails-after-dynamic-disk-conversion.html)

---

### Post by ibates on 2009-11-25
Thanks

Firstly- no, the disk is not dynamic.

I did get the Super Grub Disk and booted into Ubuntu.

Next; when I run the command sudo grub-install /dev/sde (sde is shown in the Palimpsest Disk Utility as the HDD descriptor for my Ubuntu HDD) I get the following dialogue

[I]grub-probe: error: Cannot find a GRUB drive for /dev/sde1.  Check your device.map.

Auto-detection of a filesystem module failed.[/I]

When I change the disk parameter to /dev/sdc (the Windows HDD), I get the same message.  What now?

---

### Post by namok on 2009-11-25
> **ibates said:**
> [I]grub-probe: error: Cannot find a GRUB drive for /dev/sde1.  Check your device.map.

Auto-detection of a filesystem module failed.[/I]

When I change the disk parameter to /dev/sdc (the Windows HDD), I get the same message.  What now?
```
sudo grub-mkdevicemap
```it generates a new device.map file.
```
sudo update-grub2
```it make a new grub.cfg file.
Restore grub to the MBR:
```
sudo grub-install /dev/sdX
```

---

### Post by ibates on 2009-11-27
Thank you NAMOK for your assistance.  This problem is solved.

Super Grub is a superb facility even if the help notes are a little difficult to wade through.

Well worth having in ones collection.

---

