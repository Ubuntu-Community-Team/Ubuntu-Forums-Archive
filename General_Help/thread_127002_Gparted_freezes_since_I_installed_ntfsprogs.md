---
title: "Gparted freezes since I installed ntfsprogs"
date: 2006-02-07
forum: General Help
---

### Post by ScottY86 on 2006-02-07
Gparted was working great until I installed ntfsprogs through synaptic.  Now, when I start Gparted it says it's scanning my disks and the progress bar is moving back and forth, but it slowly grinds my system to a complete halt and at that point I can't even move my mouse.  Finally, gnome killed itself and there was a message that ntfscluster ran out of memory.  

I've tried uninstalling and reinstalling both gparted and ntfsprogs and the same things still happen.  I have a single hard drive with an ntfs windows partition and an ext3 ubuntu partition.

Any ideas?

Thanks!
Scott

---

### Post by nanotube on 2006-02-08
have you tried just uninstalling ntfsprogs? or can't you live with just read only access to ntfs?

---

### Post by ScottY86 on 2006-02-08
Well, I wanted to resize my windows partition and I'm not hardcore enough to do it another way :-)

---

### Post by nanotube on 2006-02-08
heh ic. :) well according to this thread: [http://ubuntuforums.org/showthread.php?t=126334&highlight=resize+ntfs](http://ubuntuforums.org/showthread.php?t=126334&highlight=resize+ntfs)
you can easily resize your ntfs partition with the gparted livecd. try it.

---

### Post by plors on 2006-02-08
[QUOTE=ScottY86]Gparted was working great until I installed ntfsprogs through synaptic.  Now, when I start Gparted it says it's scanning my disks and the progress bar is moving back and forth, but it slowly grinds my system to a complete halt and at that point I can't even move my mouse.  Finally, gnome killed itself and there was a message that ntfscluster ran out of memory.  

I've tried uninstalling and reinstalling both gparted and ntfsprogs and the same things still happen.  I have a single hard drive with an ntfs windows partition and an ext3 ubuntu partition.

Any ideas?

Thanks!
Scott[/QUOTE]

Interesting...
please consider filing a bug with detailed information about this problem (see [http://gparted.sourceforge.net/bugs.php]("http://gparted.sourceforge.net/bugs.php"))

---

