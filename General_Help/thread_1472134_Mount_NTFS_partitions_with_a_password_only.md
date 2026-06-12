---
title: "Mount NTFS partitions with a password only"
date: 2010-05-04
forum: General Help
---

### Post by Mark Goldshtein on 2010-05-04
Hello, forum!
 

 I have U1004 dual boot with MSW7 and sometimes want to mount those NTFS partitions for mostly reading operations. Ubuntu makes it easy by a single click in Nautilus. How to change this behavior and allow mount NTFS partitions with user's password only, like sudo behavior, for example?
 In addition, how to mount them read-only?
 

 Note: I mount those NTFS partitions occasionally and there is nothing in fstab about it.
 

 Thanks!

---

### Post by StuartN on 2010-05-04
> **Mark Goldshtein said:**
> In addition, how to mount them read-only?

You can find the UUID of the NTFS partition with the command **sudo blkid** - copy this value, or open a second terminal so that you can see it. Edit fstab with **sudo gedit /etc/fstab** and add a new line to the bottom something like this:

```
# New entry for mounting NTFS at startup
UUID=2a960adb-81b4-4a6a-a3ce-7cbeadfb2331 /media/NTFS-partition            ntfs-3g    ro              0       0
```

The NTFS partition would be mounted readonly at /media/NTFS-partition at every startup.

---

### Post by Mark Goldshtein on 2010-05-04
> **StuartN said:**
> The NTFS partition would be mounted readonly at /media/NTFS-partition at every startup.

Probably, I did not made myself clear.
I do not need to mount NTFS partitions every time I boot the system up. I need to mount them occasionally, with password request and read-only access.

---

### Post by StuartN on 2010-05-04
> **Mark Goldshtein said:**
> Probably, I did not made myself clear

I have not tried it, but adding **noauto** to the mount options in fstab should mean that the drive requires explicit mounting, i.e. is not mounted at startup. Option **nouser** (the default) should require a sudo password to mount the drive (although, of course, any user can mount an NTFS partition and this is merely pasting fake security on top of an insecure partition).

I don't know if Mount Manager packages up this functionality in a usable form.

---

### Post by dino99 on 2010-05-04
mountmanager (if installed and tweaked with your prefs) do that smootly

---

### Post by Mark Goldshtein on 2010-05-05
Thanks to everyone! Happy to have many ways to resolve a problem. That is Open Source, right? :)

---

