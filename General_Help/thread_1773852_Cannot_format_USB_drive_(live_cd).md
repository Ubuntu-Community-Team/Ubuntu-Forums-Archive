---
title: "Cannot format USB drive (live cd)"
date: 2011-06-02
forum: General Help
---

### Post by whalogreg on 2011-06-02
Long story short.. I took my 4GB usb drive and installed Fedora w/Gnome Shell as a live cd to give Gnome Shell a try. I now cannot format the usb drive, as my system sees it as a cd-rom. Gparted simply gives me an ambiguous error. I'd really like to not spend more money on a usb drive, even as inexpensive as they are now-a-days.. Anyone know where I should start with this?

---

### Post by jamesisin on 2011-06-02
It's been a long time since I used a USB drive that way, but doesn't it have a small partition that makes the OS think it's a CD?  Or maybe it's a file...

Is the drive mounted as read-only?  Can you manually mount it as read-write?

---

### Post by MagneticFlux on 2011-06-02
What does running ```
fdisk -l
```on the terminal give you?

---

### Post by whalogreg on 2011-06-02
Ok, this is odd... I tried formating it with Gparted again, and it seemed to work.. to an extent. I formated it to Fat32. I can now create folders, read and write files, but I cannot rename the drive or change the permissions..

---

### Post by MagneticFlux on 2011-06-02
You may try creating a new partition table on GParted.(Under Device menu)

---

### Post by jamesisin on 2011-06-02
Are you attempting to make all of these changes in GParted?  If you are trying to change them in Nautilus (or similar) you will run into permissions issues without gksudo; similarly without sudo on the command line.  (GParted runs under gksudo and so should not have permissions issues.)

---

### Post by life in color on 2011-06-23
Well if you want to rename the USB drive you could open GParted and right click the device then select "label" and voila! I know that works for ext2 and ext3 partitioned disks though I don't know about ntfs and others, give it a shot though.

---

