---
title: "need to move ubuntu install do different partition"
date: 2009-12-28
forum: General Help
---

### Post by onesojourner on 2009-12-28
I need to figure out how to move my current ubuntu install to a different partion on my hdd or resize the partition that it is on. Can some one walk me through the process?

---

### Post by avtolle on 2009-12-28
> **onesojourner said:**
> I need to figure out how to move my current ubuntu install to a different partion on my hdd or resize the partition that it is on. Can some one walk me through the process?
If you are trying to resize the partition, boot from the Live CD to do so (whether the Live CD is Ubuntu, or Gparted), as the drive cannot be mounted to do this. I've never attempted to move my install to a different partition, so cannot help there.

---

### Post by audiomick on 2009-12-28
If you can get away with just resizing, that will be a lot simpler. It should leave the boot loader, grub, unaffected. If you move it, you will also  have to reset that.

You can re-size with the gparted live CD, which you can get here.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It will most likely be the easiest choice to do it from a live CD because the partition has to be unmounted to be altered.

The ubuntu live cd also has gparted on it, but some people think that the gparted one works better.

---

### Post by synapsys on 2009-12-28
I believe the easiest thing to do would be to resize the partition using gparted. If you're wanting to resize the root partition, you will need to do this from a ubuntu live cd or gparted live cd. Once you fire up gparted, it is pretty self explanatory, you will of course want to **back up** all important data any time you go messing around with partitions.

---

### Post by onesojourner on 2009-12-28
> **synapsys said:**
> I believe the easiest thing to do would be to resize the partition using gparted. If you're wanting to resize the root partition, you will need to do this from a ubuntu live cd or gparted live cd. Once you fire up gparted, it is pretty self explanatory, you will of course want to **back up** all important data any time you go messing around with partitions.

I have read that there can be issues with ext4. Is this something I need to worry about or has it been fixed?

---

### Post by avtolle on 2009-12-28
I'm using ext4 on three different 9.10 installs, and haven't been confronted with any problems. YMMV.

---

### Post by synapsys on 2009-12-28
> **onesojourner said:**
> I have read that there can be issues with ext4. Is this something I need to worry about or has it been fixed?

I couldn't tell you, I've done it a couple times with no problems, but that doesn't mean it's impossible to have problems. If you're really worried about it, and you have enough space, you can make a copy of your partition and use that to play around with. 

You can resize the new partition and tell fstab to mount the new partition instead of the old one. If everything works, delete the old one, if it fails miserably, delete the new one and restore fstab to the original.

---

