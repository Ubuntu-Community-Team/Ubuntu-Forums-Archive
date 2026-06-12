---
title: "Accidentally overwrote modprobe.d/aliases"
date: 2010-02-22
forum: General Help
---

### Post by abstractlogic on 2010-02-22
I was trying to edit Modprobe.d/aliases and accidentaly overwrote the file after i backspaced it all.

I'm running Karmic.  Any way someone can paste the contents of the file?

---

### Post by spiderbatdad on 2010-02-22
Using your terminal navigate to /etc/modprobe.d and run ```
ls -al
``` I believe you will find the system made a backup copy for you.

---

### Post by abstractlogic on 2010-02-22
how would i access that in terminal?

---

### Post by spiderbatdad on 2010-02-22
```
cd /etc/modprobe.d
``` cd command = change directory. Looks like no luck though (maybe). Ubuntu used to automatically backup some system files when edited...I don't know why. But certain files when edited would get re-listed with ~, so you might see aliases~ or a dot (.) followed by a date. Sorry I don't have aliases in /modprobe.d or I would paste for you. I just tried some editing in the directory, no backups were created...sigh.

HMMM. just tried editing system file again with gksu nautilus and a backup was created...
blacklist.conf~
So in future when editing system file rename the original as a backup or use nautilus and gedit as root.

---

