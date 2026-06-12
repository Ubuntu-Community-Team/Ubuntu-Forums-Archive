---
title: "Removed game &quot;Golly&quot; now all my files are gone. Really need help."
date: 2009-08-20
forum: General Help
---

### Post by shanee753 on 2009-08-20
I removed Golly from applications > add/remove.
While it was removing I was looking though my folders. Suddenly they all disappeared, at the same time the pop up appeared to tell me Golly was removed.
This is a Huge bug or deliberate virus like attack?
I would like to know if there is anyway I can get my files back?
My documents, my music and my pictures are all totally empty. Basicly everything at home/ellipsis/ that don't start with a "." is gone although all the folders are still there.
edit: Oh and it seems permission is denied when I try to do anything like move a file.

I would be very thankful if anyone could help me.

---

### Post by philinux on 2009-08-20
Sounds unrelated. Try logging out then back in again. Or reboot.

---

### Post by shanee753 on 2009-08-20
I have tried both. Also my music program can't load the music files anymore.
Thanks though.
edit:
Before hand I had been changing a few files in root, I also did "chmod 666" on a folder.
I think this is unrelated though as the files disappeared after I removed the game.
Any one else have any ideas? Much appreciated!

---

### Post by shanee753 on 2009-08-21
EDIT: THANK GOD! fixed. Turns out this whole thing was a permission **** up. The uninstall had somehow made my home folder unacceptable by me. I did "Sudo CHMOD 644" to it and now everything is back. Thanks Philinux for trying to help and thank god I didn't format that partition before I worked this out.

---

