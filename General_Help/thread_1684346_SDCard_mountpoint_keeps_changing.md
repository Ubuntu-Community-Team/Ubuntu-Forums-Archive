---
title: "SDCard mountpoint keeps changing"
date: 2011-02-09
forum: General Help
---

### Post by Nathanael Culver on 2011-02-09
After upgrading to KDE 4.6 recently, my sdcard's mountpoint changed from /media/disk to /media/<uuid>, wreaking havoc with a number of scripts. I updated the scripts, and all was fine for a couple of weeks. Then last night it suddenly began appearing at /media/på @DOKUWI/ (??? - I have no idea why or how or where the heck uDev is pulling *that* label from).

The sdcard is fat32. As far as I can tell, it has no volume label (I've tried setting the volume label with mtools, but I keep getting "cannot intialize drive" errors). 

I'd tried adding this to fstab:

/dev/sdb1       /media/sdcard1  auto    rw,auto,user,sync       0       0

but when I rebooted my system, the sdcard slot shifted from sdb1 to sdc1. But I don't think fstab is the right place to be addressing this issue, anyway.

I'm getting pretty tired of chasing my sdcard all over my system. I want to ensure that my sdcard slot consistently mounts at the same mountpoint every time, not matter which sdcard I plug into it (so mounting by uuid won't work). 

--Nathanael

---

### Post by Nathanael Culver on 2011-02-09
Bump

---

### Post by tredegar on 2011-02-09
The solution to this is to write a **udev** rule. This is (partly) what udev is _for_.

Here are some links to help you:

[Link1]("http://www.reactivated.net/writing_udev_rules.html") (A bit old, but the original HOWTO)
[Link2]("http://www.kevinblake.co.uk/auto-running-commands-when-plugging-in-usb-drives-with-udev-in-linux/732/")
[Link3]("http://www.linux.com/news/hardware/peripherals/180950-udev")

---

### Post by mcduck on 2011-02-09
The easy solutions are these:

1. Label the card. If you can't do that on your Ubuntu system (Although it hsould work) then perhaps somebody you know has Windows or OSX?

2. Use fstab. You can configure your card there using UUID instead of device name (which is what you should always do when configuring drives in fstab anyway...)

---

### Post by Nathanael Culver on 2011-02-10
OK, borrowed time on a friend's Windows machine, labeled the card, and it now automounts where I want it. I'm trying to write a udev rule to autorun a backup script, but that's a subject for another post, I guess. Thanks for all your help.

--Nathanael

---

