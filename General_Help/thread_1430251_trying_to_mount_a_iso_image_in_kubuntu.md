---
title: "trying to mount a iso image in kubuntu"
date: 2010-03-15
forum: General Help
---

### Post by dmdevotee on 2010-03-15
hi everybody

to mount an iso file, i type in terminal:

sudo mount -t iso9660 -o loop "/media/WD10EADS/Software/sistemas operativos/kubuntu-9.10-desktop-amd64.iso" /media/prueba

the first time i did this, there was no error, but /media/prueba were empty

i typed it again, and it gives the error message:

mount: according to mtab /media/WD10EADS/Software/sistemas operativos/kubuntu-9.10-desktop-amd64.iso is already mounted on /media/prueba as loop



why it doesn't mount?? thanks!


edit: solved, but don't know why...now the folder is not empty, but it was empty minutes after typing the mount command. maybe it takes some time to mount?

---

### Post by l4zy on 2010-03-15
It seems that it's allready mounted.

Try to umount it first then remount. If it says that cannot umount since device is busy use -l swich.

---

