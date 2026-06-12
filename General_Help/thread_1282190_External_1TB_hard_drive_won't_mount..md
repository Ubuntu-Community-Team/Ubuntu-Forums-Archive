---
title: "External 1TB hard drive won't mount."
date: 2009-10-04
forum: General Help
---

### Post by manji_kun on 2009-10-04
good morning my fellow Ubuntu users! i come bearing gifts.. ok i lie on the gifts thing, i ate the cookies on the way here.

however, i do require the assistance of someone more knowledgeable than i am.

ia friend of mine has a 1TB external USB hard disc drive, (NTFS format) he doesn't want to re-format  it for linux since it has a ton of back up files stored on it that he doesn't want to lose (mostly not porn) but everytime i try to mount it for him i get is 

[IMG]http://i26.photobucket.com/albums/c115/jinto_lin/TryingToExtractATar.png[/IMG]




anyone know how i can force it to mount? (also, let me know if i left out anything important)

---

### Post by crolanx on 2009-10-04
I wonder  why you are trying to do something with fuse. It already should be installed correctly. :confused:

Instead, to mount the disk manually, try something like
```
sudo mount -v -t ntfs /dev/sdb1 /mnt
```.

( Most likely that you'll have to replace /dev/sdb1 with the appropriate device file. )

---

### Post by renkinjutsu on 2009-10-04
and if you want write support, mount with `-t ntfs-3g` instead of just `-t ntfs`

---

### Post by manji_kun on 2009-10-04
thats what i was saying, my 120gb isn't external, but it's not set as a slave and my computer read it instantly, i wonder if it being USB has anything to do with not being mounted.

---

### Post by scouser73 on 2009-10-04
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

