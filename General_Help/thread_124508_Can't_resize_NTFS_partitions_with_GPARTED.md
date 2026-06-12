---
title: "Can't resize NTFS partitions with GPARTED?"
date: 2006-02-01
forum: General Help
---

### Post by Curlydave on 2006-02-01
I'm trying to resize my NTFS partion using parted, but resizing is not an option. There is a triangle with an exclamation point in the middle next to the partition name saying the following: "Unable to read the contents of this file system! Because of this, some operations may be unavailable.

I know I can read it because it mounts and i can browse it, but then I can't resize it because it's mounted. Ugh.

What's up?

---

### Post by earobinson on 2006-02-01
ntfs partitions are unsuported as far as I know. try partition magic or something else!

EDIT: yup im wrong!

---

### Post by Lord Illidan on 2006-02-01
You should be able to resize NTFS partitions. Have you tried the Gparted live cd?

---

### Post by steve.horsley on 2006-02-01
You could always unmount it and then re-size it.

From the command line, **sudo umount /dev/hda1** or whatever it is.

---

### Post by az on 2006-02-01
[QUOTE=Curlydave]I'm trying to resize my NTFS partion using parted, but resizing is not an option. There is a triangle with an exclamation point in the middle next to the partition name saying the following: "Unable to read the contents of this file system! Because of this, some operations may be unavailable.

I know I can read it because it mounts and i can browse it, but then I can't resize it because it's mounted. Ugh.

What's up?[/QUOTE]
You can't make changes to the partition table when you have a partition mounted on it.  You need to run froma live cd *and* unmount your swap (the live cd uses your drive<s swap partitoin, if it finds one)

sudo swapoff -a

You need ntfsfsprogs to add the ntfs functionality to gparted.

sudo apt-get install ntfsprogs

---

### Post by lamego on 2006-02-01
After installing ntfstools you can also resize using the ntfsresize command line tool.
On the shell:
man ntfsresize

---

### Post by Curlydave on 2006-02-01
Hey, thanks for the info guys! I actually stumbled upon ntfsprogs in synaptec and nstalled it, and used it. It resized my NTFS partition alright, but the space I removed from it disappeard and no free space was created! Is that wack, or what? Windows booted OK though, so nothing lost. I used it again only this time wihtout specifying a size and it put it back to its normal size.

I tried gparted again, and now it works though! :) It resized my partition and created free space with it. Yay!

---

### Post by plors on 2006-02-01
all those issues with resizing should be gone in the latest gparted (0.2)

---

### Post by az on 2006-02-01
[QUOTE=Curlydave]Hey, thanks for the info guys! I actually stumbled upon ntfsprogs in synaptec and nstalled it, and used it. It resized my NTFS partition alright, but the space I removed from it disappeard and no free space was created! Is that wack, or what?![/QUOTE]

You shrunk the filesystem, but not the partition.

---

### Post by ianimal on 2008-02-24
Unmount the drive then run:

sudo ntfsresize -s 40G /dev/sda2

Obviously change 40G to the desired size and /dev/sda2 to the desired partition device.  Once this is complete reopen GParted and the drive will still be the same size but there will be no error on the drive and you can now use gparted to resize it.

---

