---
title: "Error trying to remove a directory in a USB memory live"
date: 2009-08-30
forum: General Help
---

### Post by ZequeZ on 2009-08-30
I've installed Ubuntu on a USB memory, though "uSbuntu Live Creator" in a Window$ computer... Everything is ok, until I tried to install LAMPP into the "opt" directory...

The first thing I thing I've to say is that the USB memory is in Fat32 =/. I want to be able to use it as a data carrier and as a portable OS.

First time I try to copy LAMPP into the "opt" directory, I got some errors, soy I used "rm -R" to remove the entirely directory, but I get an error in SOME directories:

"rm: cannot remove directory '<Directory>' : Input/output error"

How can I solve this error? Because when I try to copy files again I got the same "Input/output error" but with cp command :S.


Thanks.
And sorry if I made some English sintax errors =/.

---

### Post by uylug on 2009-08-30
Getting the same error here.

I often get "Folder not empty" as well when a folder **is** empty and there are **no** hidden files or anything.

And this does not seem to work

```
sudo rm folder -r
```

---

### Post by The Cog on 2009-08-30
You could try to fsck it:
**sudo fsck.vfat /dev/sdb1** (or whatever device it is).

---

### Post by ZequeZ on 2009-08-30
> **The Cog said:**
> You could try to fsck it:
**sudo fsck.vfat /dev/sdb1** (or whatever device it is).

How do I get a list of the devices connected? Ubuntu is installed in the USB memory, can I do this anyway?

Sorry, I'm new on Linux :S.

---

### Post by The Cog on 2009-08-31
**sudo fdisk -l** will list all the connected drives. If you have any doubt about which drive it is, don't try it! Actually, **df -h** probably gives a prettier output, Do it without the drive connected, then again with it connected and see which is the new device.

Oh, and you will need to unmount the drive before you can fsck it. Having found out which device it is, either **sudo umount /dev/whatever** or right-click the icon and choose unmount.

---

