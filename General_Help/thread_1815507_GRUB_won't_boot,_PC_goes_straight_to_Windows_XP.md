---
title: "GRUB won't boot, PC goes straight to Windows XP"
date: 2011-07-31
forum: General Help
---

### Post by gattz on 2011-07-31
I just did a clean install of Windows XP on my PC and then installed Ubuntu 10.10 alongside it. When I boot my PC it just goes straight to XP, and the GRUB boot screen doesn't appear. From what I've read, it seems I need to get the GRUB screen to appear to be able to select which OS I want to use. I've never tried doing this before so I'm pretty lost. Any help would be very appreciated.

---

### Post by Bapun007 on 2011-07-31
at install time i think you install grub in the root of ubuntu other then mbr . it is better you do a reinstall with placing grub at mbr.

---

### Post by gattz on 2011-07-31
I was thinking I'm going to have to reinstall XP and Ubuntu also. How do I go about doing what you suggested exactly?

Also, I used the Super GRUB2 Disc to force GRUB to boot. It detected XP and Linux, but when I try to run Linux this message stops me:

VFS: Cannot open root device "UUID=2b6b7ef6-0bdf-4553-b124-387327d4d801" or unknown-block(0,0)

Please append a correct "root=" boot option; here are the available partitions:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

---

### Post by gattz on 2011-07-31
I was able to get Ubuntu to boot with the CD and install GRUB 2, but it still doesn't appear on boot. Any help here guys?

---

### Post by oldfred on 2011-07-31
If grub has not found the windows install, it only sees Ubuntu so it knows you do not want menu, normally. If you hold shift from BIOS util menu appears, you should get menu.

This should find your windows install from your working Ubuntu:

```
sudo update-grub
```

---

