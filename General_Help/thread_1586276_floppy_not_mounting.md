---
title: "floppy not mounting"
date: 2010-10-01
forum: General Help
---

### Post by nerdy_kid on 2010-10-01
Running Lucid with GNOME and my floppy wont mount.  It will mount if I manually do sudo mount -o loop /dev/fd0 FOLDER but it will not mount from GNOME's "places" menu.  anything I can throw in fstab to coerce it to work?

thanks

---

### Post by nerdy_kid on 2010-10-02
i know floppys are "dead" but someone has to know!
bump :)

---

### Post by nerdy_kid on 2010-10-04
bump

---

### Post by philinux on 2010-10-04
> **nerdy_kid said:**
> i know floppys are "dead" but someone has to know!
bump :)

I reckon you need to install [fdutils]("apt:fdutils")

This package contains utilities for formatting extra capacity
disks, **automatic floppy disk mounting and unmounting**, etc.

---

### Post by nerdy_kid on 2010-10-04
> **philinux said:**
> I reckon you need to install [fdutils]("apt:fdutils")

This package contains utilities for formatting extra capacity
disks, **automatic floppy disk mounting and unmounting**, etc.

thanks for that; but I can get fstab to mount it if I need it.  The issue seems to be GNOME; cause I can get the floppy to mount (with the -o loop option) its just that GNOME cant mount it.  It used to work; but something broke I guess.

---

### Post by TerrieG on 2010-10-05
I am a novice.  I am not able to mount a floppy from a terminal screen by typing "mount /dev/fd0".  Neither can I go to the panel where it shows the label floppy and ask it to mount a floppy (maybe that is what you are talking about GNOME?)  

I can't mount any of my floppies so I know it just isn't a problem with one disk.  It has been a while since I have mounted a floppy - actually I have installed a few upgrades since I last did it.  

the entry in the file /etc/fstab says

/dev/fd0 vfat rw,user,noauto,exec,utf8 0 0

Any suggestions?

---

### Post by TerrieG on 2010-10-05
One more thing I tried.

"fsck /dev/fd0"  returns

open: Permission denied

how do I set proper permissions?  Didn't think I had changed any permissions.

---

### Post by TerrieG on 2010-10-05
I found another posting that describes the problem I am having.  

I got around the problem by logging on as root and 

commenting out the /dev/fdo line in fstab
then
sudo mount -t vfat /dev/fd0 /media/floppy0

then sudo umount /dev/fd0

when I was done.

Shouldn't have to do all this - and yes it had something to do with some updates I installed.

It probably doesn't answer your original question.

---

### Post by nerdy_kid on 2010-10-06
no it doesn't answer my question; but it is good to know that I am not the only one dealing with this.  Maybe we should report a bug...

---

### Post by KirbySmith on 2010-10-09
FWIW, my floppy drive had no karma running 9.10.  The method of TerrieG (except I set vfat to auto) and others in historical threads made it possible to see the contents of many of my floppies.  I also made myself and root members of the floppy group, which seems to solve the problem of having to use nautilus as root to copy anything.  

I haven't tested formatting yet and so far this is only confirmed on Desktop2 (see below).

However, as many others have pointed out in many threads, this process causes a floppy0 drive to appear in nautilus and on the desktop; the floppy directory remains empty.   Disk Utility continues to assert no media, even though checking for media in Disk Utility causes the floppy drive to run briefly.  This may be the result of active, passive, or accidental deletion of required fd functionality in Karmic.

In my opinion, the greater convenience of USB thumb drives is not justification for inerting floppy disk capability that functioned in earlier versions.  As far as I know, certain activities one might run from a limited boot, such as the Spinright disk checking utility, require a floppy drive in the boot order.

kirby

---

### Post by Objekt on 2010-10-11
As with other proposed solutions, the steps in #8 did nothing for me.

I can access my floppy drive in Ubuntu 10.04, although I did have to manually revert and lock a package (udisks) which is not present in Ubuntu 9.10.

---

### Post by KirbySmith on 2010-10-11
I forgot to include that I also inserted "floppy" into /etc/modules.

Both desktops are now floppy drive functional, if one calls having to manually mount and dismount functional. 

Nonetheless, Objekt, I suspect that 10.4 is sufficiently different that 9.10 solutions are inadequate.  Advice in threads addressing 10.4 specifically should be used instead of threads applicable to versions through 9.10.

kirby

---

