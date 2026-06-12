---
title: "Ubuntu won't let me set files as executable."
date: 2011-10-17
forum: General Help
---

### Post by Bluehotdog5 on 2011-10-17
so I was trying to set an executable file to run under wine, so I tried going to properties > permissions then checking the box, but it just unchecks itself. I then tried using the terminal with the chmod command, and that did nothing.
This is really annoying, anyone know why its doing this?

---

### Post by Meelad on 2011-10-17
> **Bluehotdog5 said:**
> so I was trying to set an executable file to run under wine, so I tried going to properties > permissions then checking the box, but it just unchecks itself. I then tried using the terminal with the chmod command, and that did nothing.
This is really annoying, anyone know why its doing this?

Is your file located on an NTFS partition or a Windows partition? If so you can't change the file permissions. You have to copy it to an Ext4 partition to be able to set its permissions and run it..

---

### Post by Bluehotdog5 on 2011-10-17
> **Meelad said:**
> Is your file located on an NTFS partition or a Windows partition? If so you can't change the file permissions. You have to copy it to an Ext4 partition to be able to set its permissions and run it..

I did the same thing with the setup.exe on the install disk and it did the same thing

---

### Post by mc4man on 2011-10-17
It's not that a .exe needs the X bit set - it's the cautious-launcher wine uses in some ubuntu versions
lots of ways around the nonsense - a couple below

If not on 11.10 then simply right click on the .exe > open with > other application > use a custom command
For the command just use this
wine

After that any time you r click on an .exe you'll see 'wine' as a choice, pick that.

If you want for cd's you can also create a static mount point & an fstab entry for the drive that auto give exec permission
(the first way should work on cd's/dvd's, the fstab is more a convenience, though has some advantages for using disks in wine

---

