---
title: "Broken filesystem"
date: 2011-05-18
forum: General Help
---

### Post by Tryfon on 2011-05-18
Hi. I have a broken Ubuntu installation on an ext4 partition. It fails to startup, seems like a broken filesystem. I boot live with an Ubuntu cd and try to check the filesystem with fsck and it responds that it is busy for no apparent reason. I try to mount it and it hangs without any response. Any ideas???

---

### Post by dabl on 2011-05-18
The [[COLOR="SeaGreen"]**Parted Magic**[/COLOR]](http://partedmagic.com/doku.php?id=downloads) Live CD or USB stick has a bunch of utilities including disk recovery tools, as well as Gparted.  I would advise you to boot the computer with a Parted Magic Live CD, then use the partitioning tool (Gparted), right-click the problem filesystem, and choose "check".  In the graphic window there will be details available (you have to expand the message), and possibly there will be useful information in the list of details.

---

