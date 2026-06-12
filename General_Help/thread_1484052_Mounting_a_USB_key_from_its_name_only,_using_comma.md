---
title: "Mounting a USB key from its name only, using command line or text interface"
date: 2010-05-15
forum: General Help
---

### Post by vivien` on 2010-05-15
Is there a way to mount a USB key just from its name, and without a GUI?

Take most graphical file managers: they offer you to mount a USB key (also a CD) just by clicking on its icon. This is pretty convenient! Usually, you even have the name and size of the key before it is mounted. At least this is the case in Thunar, for example.

How to do the same from command line (cli) or in a text-mode interface? The cli tool or the text interface would show the list of devices that can possibly be mounted, and would offer to mount them.

---

### Post by dv3500ea on 2010-05-15
```
sudo mount -t vfat /dev/disk/by-label/name /media/name
```
replacing name with the drive label and assuming the filesystem is FAT or FAT32 (replace vfat with the correct filesystem, eg. ext3 otherwise). You may need to run ```
sudo mkdir /media/name
``` again replacing name, before you mount. Run ```
ls /dev/disk/by-label
``` to get a list of drive labels.

---

### Post by vivien` on 2010-05-15
Thanks for the pointers.

From a discussion on IRC (#linux on freenode), I got this line:

> pmount-hal "$(hal-get-property --udi $(hal-find-by-property --key info.product --string "$label") --key block.device)"
where $label is the volume name.

It requires pmount-hal that is part of the package pmount.

---

