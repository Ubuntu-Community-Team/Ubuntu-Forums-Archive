---
title: "ubuntu fdisk -f"
date: 2010-02-27
forum: General Help
---

### Post by gaminggoose on 2010-02-27
I need to set a MBR to a template that i have.

on osx the comande is sudo fdisk -f boot0 -u -y [template file location]

is there a unbuntu way of doing this?

---

### Post by spiderbatdad on 2010-02-27
linux definitely has the fdisk utility. It can be very destructive. When I have used it, it has been on external devices, unmounted, I believe. So a live cd would be a way of running on your primary hdd. Unless you want to edit another unmounted partition on the same hdd.
Usually the command goes something like:
sudo fdisk /dev/sdaX
where X is the partition number. Typing m will list available options and q will quit without writing to the disk.

---

### Post by gaminggoose on 2010-02-27
thanks for the tip,
however the -f function isn't part of linux fdisk,

is there another way to do the same thing in linux?

---

### Post by gaminggoose on 2010-02-27
thanks for the tip,
however the -f function isn't part of linux fdisk,

is there another way to do the same thing in linux?

---

### Post by spiderbatdad on 2010-02-27
no idea. even the unix manpages for fdisk do not show a -f option.
There is also parted, cfdisk and other programs you can look into.
Sorry not of more help.

---

