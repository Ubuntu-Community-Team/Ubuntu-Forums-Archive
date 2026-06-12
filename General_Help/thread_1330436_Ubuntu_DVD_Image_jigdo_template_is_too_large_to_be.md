---
title: "Ubuntu DVD Image jigdo template is too large to be useful"
date: 2009-11-18
forum: General Help
---

### Post by argie on 2009-11-18
Why is the Ubuntu jigdo template file 1.2 Gb in size? By comparison Debian's jigdo template is 29 Mb in size. Surely the Ubuntu DVD isn't so terribly different? If I were to download the template files for all the Ubuntu CDs I still wouldn't match the size of the Ubuntu DVD template file.

Take a look at the difference between [Ubuntu 9.10]("http://cdimage.ubuntu.com/dvd/20091117/") and [Debian 5.03]("http://cdimage.debian.org/debian-cd/5.0.3/amd64/jigdo-dvd/"). I would report a bug but I have no clue under what category to place it on launchpad.

EDIT: Never mind, it is [#484911]("https://bugs.launchpad.net/ubuntu-website/+bug/484911").

---

### Post by Lucrus on 2010-04-22
I used to download Debian with jigdo and noticed just the same problem when I tried with Ubuntu. I'm going to file a bug on launchpad in jigdo, maybe the mantainer will move it to the correct place.

---

### Post by Lucrus on 2010-04-22
The bug was already filed:

[https://bugs.launchpad.net/ubuntu/+source/jigdo/+bug/55925](https://bugs.launchpad.net/ubuntu/+source/jigdo/+bug/55925)

Unfortunately there's nothing that can be done about it, the problem is Ubuntu ships a live filesystem in squashfs format and jigdo can't create a squashfs from debs. Only possible solution: use something else, jigdo was not designed for that job.

---

