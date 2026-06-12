---
title: "/media/ NTFS drive music library problems !"
date: 2011-07-24
forum: General Help
---

### Post by RaiGal on 2011-07-24
Hello,
I have been experiencing problems with every library style music manager I had come across. The apps I have been using are quod libet, gmusicbrowser and rhythbox.

Thing is, that even though I get to scan my drive for music files and eventually these get indexed in the program, at the next reboot the library is kinda broken, the program will say this file does not exist even though nothing has changed. Also,it may occasionally play some songs from the last indexing but most of them are found as "dead" links. I came to a conclustion that this might be caused by the fact that all my music is at an NTFS drive which is mounted automatically at every boot as /media/. 

Is there any way to make these permanent instead of auto - mounting/unmounting every time?

I haven't found any way to handle this and rescaning a music library of 35.000 songs every single time is very tiring.

Thank you in advance :)

---

### Post by mikewhatever on 2011-07-24
Other partitions are usually mounted under /media/mount-point (for exaple: /media/NTFS). If a partition is labeled, the mount point is usually the same as the label, and if not, then a generic 'disk1' or something like that. Have you done something for it to mount under /media and not under /media/mount-point?

---

