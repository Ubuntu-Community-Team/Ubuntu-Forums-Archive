---
title: "RAID 0 Dual Boot Install"
date: 2012-09-29
forum: General Help
---

### Post by abney317 on 2012-09-29
I've got 2 SSDs in a raid 0 set up. I tried installing Ubuntu from the liveCD on a USB, but it just stops at the boot screen (logo with the loading dots) and never does anything else.

Is it possible to have a dual boot set up with Windows 7 and Ubuntu with raid?

Here's some of my specs if they help with anything...
[IMG]http://imageshack.us/a/img42/9636/specst.png[/IMG]

---

### Post by oldfred on 2012-09-29
I do not know RAID and am not one that suggests RAID for most desktops. Servers may need RAID to support many users. If using RAID you have to use Alternative installer as it has the extra RAID drivers.

Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

Are you in UEFI mode?

UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)

You also have both nVidia and Intel. You need to select one and install. And you probably need nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by abney317 on 2012-09-29
I'm using a laptop... but anyways, it sounds like this isn't a normal thing to do. So unless there is a know way of making this work I guess I won't mess with it

---

