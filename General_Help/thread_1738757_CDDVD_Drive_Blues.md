---
title: "CD/DVD Drive Blues"
date: 2011-04-25
forum: General Help
---

### Post by ruff1298 on 2011-04-25
Terminal Message:

ramon@Garcia:~$ apt-cdrom add
Using CD-ROM mount point /media/cdrom/
Identifying.. [10af248f064665b7d74d950f59ab0d16-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
Using CD-ROM mount point /media/cdrom/
Identifying.. [10af248f064665b7d74d950f59ab0d16-2]
Scanning disc for index files..

W: Failed to mount '/dev/sr0' to '/media/cdrom/'
E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?
W: Failed to mount '/dev/sr1' to '/media/cdrom/'

End Terminal Message.

My CD-ROM drive no longer works, and unfortunately, my DVD/CD-ROM driver is not recognized by the terminal or apt-get. How do I disable my useless CD-ROM drive (not physically, if possible; I'm a terrible computer technician and will mostly likely fry my computer if I try), and get the terminal to mount from the DVD/CD-ROM driver?

---

