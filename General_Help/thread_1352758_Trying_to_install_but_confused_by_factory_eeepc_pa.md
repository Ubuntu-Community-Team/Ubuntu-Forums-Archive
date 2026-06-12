---
title: "Trying to install but confused by factory eeepc partitions???"
date: 2009-12-12
forum: General Help
---

### Post by blur xc on 2009-12-12
Hey there- I'm trying to dual boot  Karmic UNR and the factory install of xp on an eee pc that my daughter is getting for Christmas.

What I can't figure is the default partitioning scheme (see attached pic).  sda1 is the xp partition, sda2 has 3gb used up, but I can't see what it is.  I mounted the partition on the live usb stick, and ls -a showed nothing except . and ..

sda3 has some bmp files, fonts and other misc. junk.  I have no idea what it's for.  sda4 is anyone's guess.

I'd like to shrink the xp partition to 20-ish gb, make a 15gb for Karmic, and a home partition and a swap partion, but don't know what to do with the default partiions or the data on them.

Thanks in advance-
BM

---

### Post by jacobs444 on 2009-12-12
the last partitions are for system restore of factory default OS.

---

### Post by jacobs444 on 2009-12-12
you can safely use the second  partition without losing the restore function to put windows back on the computer or windowsxp, If you ever need to replace with windows i think you must type alt+F10 when the computer first boots. If you delete the last two partitions you will lose the equivelant of your xp/vista/7 restore disks.

xp installs default to the first partition, but you may need to reformat the second one to ntfs if you invoke the restore process.

---

### Post by blur xc on 2009-12-12
Thanks for the quick responses...  I have a usb  cd drive, so could I call Asus and ask for a system restore disk if I need it, but I probably won't.

How do I see what's on the 3gigs of used space on the 2nd partition?

If I keep the system restore partition, can I still create the three partitions I need for Ubuntu?  I wan't a separate home partition, and I'll also need a swap partition.  I've heard here and there that you can only have 4 logical (?) partition on a drive, right?

I would really like to get all this installed today...

Thanks!
BM

---

### Post by blur xc on 2009-12-12
So, if I want to keep the original restore partitions, I then have to create an extended partition for Ubuntu?  Is there any disadvantage of having ubuntu on a extended partition with three primary partions inside of that?

See screenshot-


I'm still running the live-uh-usb? and will hold off commiting partioning changes for a bit, hoping someone will chime in w/ a go or to tell me that's a stupid idea.

Thanks again for all the help.
BM

---

### Post by Chronon on 2009-12-12
I generally have an extended partition containing logical partitions.  I don't think there's any tangible drawback to this.

(You can only have 4 physical partitions.  You can have _many_ logical partitions.)

---

### Post by blur xc on 2009-12-12
> **Chronon said:**
> I generally have an extended partition containing logical partitions.  I don't think there's any tangible drawback to this.

(You can only have 4 physical partitions.  You can have _many_ logical partitions.)

Sweet, thanks.  I did some googling and didn't run across any "Don't do it!" answeres so I went ahead and did it.  It's working great, so far, except the update manager seems to be hanging, but that's for another thread.

BM

---

