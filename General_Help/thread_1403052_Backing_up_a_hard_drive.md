---
title: "Backing up a hard drive"
date: 2010-02-09
forum: General Help
---

### Post by patrickaupperle on 2010-02-09
How would one go about backing up a hard drive?
I want my Windows hard drive to be backed up, so that I can restore it onto the hard drive if the hard drive was blanked. 

If this hard drive is formatted and linux is installed on it, I want to be able to restore my current Windows partitions (Win 7 and Win XP) and probably the boot loader. I am sure this is possible, but what would be the best way to go about it?

---

### Post by ssulaco on 2010-02-09
Take a look at Clonezilla if you want to image your drive,Ive never used it,but heard good things about it
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by patrickaupperle on 2010-02-09
> **ssulaco said:**
> Take a look at Clonezilla if you want to image your drive,Ive never used it,but heard good things about it
[http://clonezilla.org/](http://clonezilla.org/)

Oh, yeah. That looks like it will work nicely. I am still open to suggestions, though. Anyone else?

If no one else posts (or if I do not like the other suggestions) clonezilla will be what I will use. Thank you ssulaco.

---

### Post by jamesisin on 2010-02-09
There is a tool called rsync (and a gui called grsync) for synking data between locations.  This is very commonly used for backing up data (especially combined with cron for keeping things on a schedule).

---

### Post by patrickaupperle on 2010-02-09
I know rsync. It is actually my primary backup solution in Linux. In this case, though, I need a full hard drive backup. I am planning on installing a few OSes over my Windows installations, then restoring my Windows installations.

---

### Post by jamesisin on 2010-02-09
It's not a free solution typically, but I really like Shadow Protect (from Storage Craft).

[http://www.shadowprotect.com/](http://www.shadowprotect.com/)

---

