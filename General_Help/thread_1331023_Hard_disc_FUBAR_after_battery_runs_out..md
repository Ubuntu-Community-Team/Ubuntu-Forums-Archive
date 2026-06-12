---
title: "Hard disc FUBAR after battery runs out."
date: 2009-11-18
forum: General Help
---

### Post by Chesh on 2009-11-18
I have been having several issues with Karmic since the beta involving my hard drive. Whenever I have to fix disc errors due to an unclean shutdown I have to run fsck manually (which is pretty ridiculous, but it gets worse).

Today, my laptop was asleep for longer than usual and I was unable to charge it, the battery ran down and when I plugged it back in and tried to boot I am greeted by the usual request to run fsck manually, only this time fsck just dies and then restarts, now my partition table looks as though it has been completely blown away (GRUB error 17).

Does anyone know what could be causing this behavior (specs at the end)? After I get this latest mess sorted out I'm going to try and fix this whole thing once and for all. It's game breakers like this that is going to keep people with even moderate technical skill away from Ubuntu and Linux in general in the future.

Lenovo Thinkpad W500
160 GB SATA running in AHTI

Will add fdisk info if anyone wants it.

---

### Post by pablo66 on 2009-11-18
I just recently had exactly the same thing happen on my Dell 620. This never happened until I loaded Karmic.

---

### Post by Chesh on 2009-11-21
Same with me, this never happened in Jaunty or any other distro.

Today my battery died again in the middle of working (I guess I have to be more careful), this time not only did I have to manually run the file system check, but even though that's done I know get a kernel panic at startup because now it seems files are missing from init which is gumming up the boot process.

There is no point in even filing a bug report since it seems anything filed that reflects negatively on the new boot process gets shots down as user error almost immediately.

---

