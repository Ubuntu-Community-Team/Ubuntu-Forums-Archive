---
title: "How do I get it to mount external drive at boot automatically?"
date: 2009-10-10
forum: General Help
---

### Post by Endolith on 2009-10-10
How do I get my external drives to mount automatically at boot, without anyone logging in locally?   (Headless server)

I don't want to manually brute force everything in fstab.  I want it to automatically detect the fs, etc and mount according to the partition label, the way it does when you log in to gnome.

---

### Post by CharlesA on 2009-10-10
I just add it to fstab, but you don't want to do that. :P

Is it mounted when you connect with VNC or SSH?

---

### Post by Bucky Ball on 2009-10-10
If it is ntfs format try using ntfs-3g. Find in Synaptics and install that and ntfs-config. You will then find the config gui in System->Admin (from memory, don't quote me). The GUI has a box which lets you enable external drives and ntfs-3g writes makes the changes you will need to get it detected.

---

### Post by Endolith on 2009-10-10
> **CharlesA said:**
>  Is it mounted when you connect with VNC or SSH?

No.  That's what I want.  I want it to mount even with no one logged in, so that when I log in over SSH, I can see the drives, or when I remotely control a daemon it can see the drives.

---

### Post by CharlesA on 2009-10-10
> **Endolith said:**
> No.  That's what I want.  I want it to mount even with no one logged in, so that when I log in over SSH, I can see the drives, or when I remotely control a daemon it can see the drives.

Gotcha. I ended up editing /etc/fstab to get that working. Maybe try Bucky Ball's suggestion?

---

### Post by Endolith on 2009-10-11
I've got FAT partitions and EXT3 partitions.  No NTFS, although who knows what I'll change it to in the future.  I want it to auto-configure without having to mess with fstab each time I change something.

---

