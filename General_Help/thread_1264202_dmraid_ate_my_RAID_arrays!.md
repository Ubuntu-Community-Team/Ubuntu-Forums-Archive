---
title: "dmraid ate my RAID arrays!"
date: 2009-09-11
forum: General Help
---

### Post by skewray on 2009-09-11
I have my root partition (normally) as a RAID-1 array using mdadm.  Out of stupid curiosity I ran the command "dmraid -r" to see what kind of fake-RAID my motherboard has.  The result is that dmraid just decided to make all of my RAID arrays into one giant fake-RAID-1 array at the "hardware" level.  Mdadm fails, since it only sees one disk, not the entire set.  If I try "dmraid -x" to delete the fake-RAID setup, it tells me that it cannot delete "nvidia" setups.  How do I make dmraid go away and return to mdadm software RAID?  I can see dmraid's new device in /dev/mapper, but I don't know how to make it go away.

Any help appreciated!

Brian

ps...removing the dmraid package doesn't appear to help.

---

### Post by mbuehl on 2009-09-11
did you try rebooting and/or calling india for answers?

---

### Post by skewray on 2009-09-11
I don't speak Hindi.

I did try the "nodmraid" kernel boot option.  It had no effect.

Brian

ps...I figured out why removing dmraid does not work, and there is nothing I can think of that will do anything about it.  The machine is booting off of a partition on one of the disks.  Then it mounts root, which is a RAID-1.  But since the whole array of disks is under dmraid, there is no way to mount any of the partitions except whatever is on the first disk. This means that the initrd file on the boot partition can't be accessed or rebuilt, so there is no way to remove the dmraid from it.

---

### Post by skewray on 2009-09-12
[http://git.debian.org/?p=users/tormod-guest/dmraid.git;a=commit;h=f333bc050a21a155a1279b5ce4271fbd43ad5c98](http://git.debian.org/?p=users/tormod-guest/dmraid.git;a=commit;h=f333bc050a21a155a1279b5ce4271fbd43ad5c98)

Apparently Debian enabled the "nodmraid" option four days ago.  I suppose I have to either wait until it flows down to Ubuntu, or rebuild my kernel.  Sigh.

---

