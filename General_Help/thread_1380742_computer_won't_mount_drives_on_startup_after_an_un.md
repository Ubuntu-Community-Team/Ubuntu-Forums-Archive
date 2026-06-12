---
title: "computer won't mount drives on startup after an unexpeted poweroff"
date: 2010-01-14
forum: General Help
---

### Post by NovaAesa on 2010-01-14
Hi all,

Last night there was a rather large thunderstorm, and my computer was on at the time. The power went out while my computer was on, and now it won't boot up.

After the GRUB screen, a white message at the bottom of the normal loading screen says somthing along the lines of "a partition listed in /etc/fstab cannot be mounted /dev/disk/by-uuid/6835blahblahblah". I chose recovery mode from the grub menu, which gave me a similar message.

> One or more mounts listed in /etc/fstab cannot yet be mounted: (ESC for recovery shell)
/home waiting for /dev/disk/by-uuid/8blahblahblah

I've googled around a fair bit, but people who got the same message were mainly those upgrading to Karmic, so a different problem. I think my problem was the fact that my computer was turned off possibly while writing and definitely without being unmounted.

So far I have tried changing /etc/fstab to refer to /etc/sda5 instead of UUID=68blahblah, but that came up with the same error.

I have looked inside the /dev/disk/by-uuid and the disk that is trying to be mounted is there (so it's not a problem with that).

Anyone have any clues as to what the problem might be?

---

### Post by NovaAesa on 2010-01-14
As an update, I have booted with a live CD, and I can mount the partition is question just fine (by clicking on its icon in Nautilus). Does this change anything?

---

### Post by NovaAesa on 2010-01-16
Nevermind, I just did a reinstall.

---

