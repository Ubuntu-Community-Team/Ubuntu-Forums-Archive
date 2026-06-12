---
title: "Need to add a CD boot option to grub2 menu."
date: 2009-12-25
forum: General Help
---

### Post by User0123 on 2009-12-25
I've read the grub2 documentation but I can't figure out how to do it.

I'm presuming this can be done by the addition of a few lines in /etc/grub.d/40_custom, I just need to know what to add :P

Thanks in advance.

---

### Post by SuperSonic4 on 2009-12-25
Why? Wouldn't it be easier to boot from CD using your computer's BIOS?

---

### Post by User0123 on 2009-12-25
> **SuperSonic4 said:**
> Why? Wouldn't it be easier to boot from CD using your computer's BIOS?


I know that in most cases it is, but I'm sure you've had the odd pesky live CD and what not that insists on being ignored and letting BIOS jump to the next device. That and selecting a menu option is a lot easier than trying to press tab, shift + F8 + ALT + Banana in less than a fraction of a second.

---

### Post by blueridgedog on 2009-12-25
This thread has plenty of working examples for booting ISO images:

[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)

---

### Post by User0123 on 2009-12-25
> **blueridgedog said:**
> This thread has plenty of working examples for booting ISO images:

[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)


That's all well and good but thats not what I asked to do.

---

### Post by blueridgedog on 2009-12-25
> **User0123 said:**
> That's all well and good but thats not what I asked to do.

Correct...but putting the ISO of the image on your hard drive and booting it would actually perform a lot better, hence my suggestion.  I could not find a way to get exactly what you were looking for, but offered it as a classic Linux solution that gets the job done, but in a different way.

---

### Post by oldfred on 2009-12-26
This is not a generic way but shows grub2 booting cds:

HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

---

