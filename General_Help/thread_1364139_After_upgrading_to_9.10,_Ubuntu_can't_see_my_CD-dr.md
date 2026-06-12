---
title: "After upgrading to 9.10, Ubuntu can't see my CD-drive."
date: 2009-12-25
forum: General Help
---

### Post by Esben Kramer on 2009-12-25
It still has cdrom and cdrom0 under media, but I suspect it's from 9.04. It doesn't even show up under the 'places' menu. I don't know how to go about fixing this?

---

### Post by john newbuntu on 2009-12-26
Stick the CD in the CD-ROM slot and type the following command from a terminal:

mount -t iso9660 -o ro /dev/cdrom /media/cdrom0

---

