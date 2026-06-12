---
title: "move os to different partition?"
date: 2009-10-30
forum: General Help
---

### Post by stuart.reinke on 2009-10-30
I'm not sure if this is possible, but if it is I would appreciate someone telling me how to do it...

I have 3 partitions on my hd. hd0,1 Ubuntu Karmic(ext4) hd0,4 Kubuntu, Jaunty(ext3): hd0,7 swap

partition 1 is primary with 4 and 7 extended.

I want to delete Karmic, and move jaunty to the primary partition. 

I took quite a while to get everything just the way I like it so if I can avoid a reinstall that would be great.

---

### Post by louieb on 2009-10-30
If the Karmic (to) partition is the same size or larger than the Jaunty (from) partition. Then Gparted can do it.
[Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm") 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by stuart.reinke on 2009-10-30
> **louieb said:**
> If the Karmic (to) partition is the same size or larger than the Jaunty (from) partition. Then Gparted can do it.
[Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm") 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

Thanks.

 I'll have to take a look. They are about the same size but one is slightly bigger than the other. (not sure which one)

---

### Post by gaussian on 2009-10-30
You can also:
1) copy (using sudo) all files of one partition to empty partition. Make sure you copy everything (including permissions etc), using rsync is one possibility
2) edit /etc/fstab to reflect new UUIDs
3) edit /boot/grub/menu.lst to reflect new UUIDs
4) reinstall grub just to be sure on the boot sector

Keep a live cd handy, so you can boot/edit the files/reinstall grub if you mess things up.

---

