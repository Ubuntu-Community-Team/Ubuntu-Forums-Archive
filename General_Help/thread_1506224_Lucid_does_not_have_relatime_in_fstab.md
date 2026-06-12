---
title: "Lucid does not have relatime in fstab"
date: 2010-06-10
forum: General Help
---

### Post by Paddy Landau on 2010-06-10
As from Hardy 8.04, Ubuntu started to [use relatime as default]("https://help.ubuntu.com/community/Fstab#Options").

I just noticed today that the entries in Lucid's default /etc/fstab do  not have relatime.

Surely this is an important omission? On slow computers, it will decrease performance, and on any computer, it decreases the life of the hard drive. That's what I had understood.

Or is there something about ext4 that makes this different?

---

### Post by Paddy Landau on 2010-06-14
Bump?

---

### Post by gmargo on 2010-06-14
"relatime" is now the default (at least for ext4).  You must specify 'strictatime' to get the traditional unix behavior.  If you do a "cat /proc/mounts" you can see relatime is in use.

---

### Post by Paddy Landau on 2010-06-14
Thanks, gmargo. I had been looking at the results of [FONT=Courier New]mount -l[/FONT], which doesn't show the relatime.

[FONT=Courier New]cat /proc/mounts[/FONT] shows extra information, and you are perfectly correct.

I shall make a note of that.

---

