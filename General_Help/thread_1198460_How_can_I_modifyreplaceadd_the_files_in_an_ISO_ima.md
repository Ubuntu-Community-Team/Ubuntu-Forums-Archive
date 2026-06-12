---
title: "How can I modify/replace/add the files in an ISO image"
date: 2009-06-27
forum: General Help
---

### Post by sefs on 2009-06-27
I have tried isomaster but that seems to be doing something weird to the iso after it re-saves it.  The ISO inquestion is a bootable ISO.  

The first weird thing is that it reduces the orginal ISO in size by up to 10MB

The second thing it does is that when the image boots it seems to cannot operate the original ISO was operating such as launching scripts.

Is there any other method?

Thanks.

---

### Post by t4thfavor on 2009-06-28
mount the iso as a "drive"

mount -t iso9660 /mmedia/iso.iso /media/iso -o loop

then put in /remove whatever you want from /media/iso, and call it a day with

umount /media/iso 

Chech that the stuff is indeed in the iso, and your done.

---

