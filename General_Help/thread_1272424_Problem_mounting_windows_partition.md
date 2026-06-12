---
title: "Problem mounting windows partition"
date: 2009-09-22
forum: General Help
---

### Post by krishnamohan on 2009-09-22
Hi..

Been wanting to get may windows partitions to automount.....

I mounted a partition by clicking on it....

went to Computer..

..right-clicked on the partition and went to properties..where under volume I had mount options....

Tried to change the mount options by putting auto in....

Now I can't seem to mount it...neither can i see anyway to change the mount settings...

I went to the \etc\fstab file but it does not seem to have anything related to the windows partitions... .

Help!!!

---

### Post by ajgreeny on 2009-09-22
Have you tried rebooting?  I can't figure out what exactly you did from your description but maybr a clean boot will help; it will certainly unmount the windows partition, but whether it stays unmounted will depend on what you did and what changes you made.

---

### Post by schmidtbag on 2009-09-22
automounting has to be done in /etc/fstab, not through the proporties of the drive.  i would completely ignore the graphical proporties, they only seem to cause problems, at least for me they have

---

### Post by krishnamohan on 2009-09-23
My windows partitions have mount options as


rw nosuid nodev noatime relatime user_id=0 group_id=0 allow_other

I tried to put in an extra option auto.....and now that partition is not mounting even if I click on it...



Given below are the contents of my fstab file..

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=26b90293-08fc-4cb4-927a-0cbdfd98d333 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=eaf8188d-beb6-4c37-bcbd-8dcd0f0b01ab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by P4man on 2009-09-23
Add the ntfs line to your fstab.
 Something like:

```
/dev/sda3       /media/windows  ntfs defaults,locale=en_US.UTF-8   0   0
```

where you replace /dev/sda3 with the actual windows drive and /media/windows with whatever (existing!) folder where you want to mount the drive.

---

### Post by abhilashm86 on 2009-09-23
hi, its better to automount all ntfs and other vfat drives during boot of ubuntu, u have a nice tool which auto [mounts it, refer this for set up]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by krishnamohan on 2009-09-26
Thanks abhilash..now everything is just fine....:)

---

