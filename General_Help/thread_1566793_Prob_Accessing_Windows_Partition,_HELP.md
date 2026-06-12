---
title: "Prob Accessing Windows Partition, HELP"
date: 2010-09-02
forum: General Help
---

### Post by grimslider75 on 2010-09-02
its not very urgent but a problem nonetheless. The accessing of the windows partition from ubuntu was fairly stable until today when i tried to access it via nautilus and as soon as i attempted to click a folder on the partition, nautilus freezes and i have to restart nautilus. This problem also occurs under *sudo nautilus*. 

ps. i'm no linux expert

it's a nstc formatted partition by the way

p.s.s: the system monitor reveals that my CPU usage is unusually high (90-100%)

---

### Post by Ocxic on 2010-09-02
try running a file system scan to make sure it hasn't gotten corrupted.

---

### Post by grimslider75 on 2010-09-02
> try running a file system scan to make sure it hasn't gotten corrupted.

Ummmm, how exactly do i correctly do this?

---

### Post by oldfred on 2010-09-03
In windows run "chkdsk /f". Although you can also use "ntfsfix" in Ubuntu:
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXY   #  X- drive Y - partition

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk".

---

