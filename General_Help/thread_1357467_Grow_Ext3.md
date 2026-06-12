---
title: "Grow Ext3"
date: 2009-12-17
forum: General Help
---

### Post by Narusegawa on 2009-12-17
Having got Karmic working nicely and a new hdd... I've freed up over 110gb of space that was to the right of my / drive.

Is it a very simple process to grow / to the right to now fill the empty space remaining now. I figure I'll need to use the LiveCD to do this as / is on this partition.

Can GParted do this without screwing the existing data?

---

### Post by Techsnap on 2009-12-17
It "Should" do this fine, but as always make a backup of anything important first!

---

### Post by warfacegod on 2009-12-17
Gparted tends to like changing permissions, as in the owner of the drive. I don't know if it will for a resize operation but it certainly will when formating. Techsnap is correct, backup is a very good idea when messing with hard drive operations.

For making a backup:
[http://ubuntuforums.org/showthread.php?t=35087&highlight=Howto%3A+Backup+restore+system%21](http://ubuntuforums.org/showthread.php?t=35087&highlight=Howto%3A+Backup+restore+system%21)

I believe the liveCD uses Gparted for resizing anyway so you can save some time by using Gparted in a normal session. Although, if your trying to resize the partition that ubuntu is installed into, you will have to use liveCD. I suggest using a usb thumb drive for that if your computer can to it, it's much faster than using an actual CD.

---

