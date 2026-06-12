---
title: "GParted not working right"
date: 2011-08-03
forum: General Help
---

### Post by conradin on 2011-08-03
For about a month GParted has been not running right for me. When I try to formate ext2/3 FS to a disk, it never completes, or hangs or then wont quit all the way when I shut it down. Then I have to use sudo pkill gparted to kill it right. Any one else having this trouble? Whats going on here? Is this some sort of kernel regression?

---

### Post by knutschr on 2011-08-03
You can't use this in partitions that i activ.
Burn this .iso and start from it.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by krytorii on 2011-08-03
Do it from a live cd, like knutschr said. You can also use the ubuntu live cd.

If you aren't trying to edit your ubuntu partition, I would still recommend trying from a live cd.

---

### Post by conradin on 2011-08-07
Separate disks, the partitions arent active, unmounted and everything. Its been screwy in live-mode too. Thing just hangs. Was there a drop in ext2/3 support??

---

### Post by ottosykora on 2011-08-07
no there is no drop in ext3 support or anything like that.

I am using mostly copy from partedmagic (bootmedia) and all works fine so far.
Things go often long with gparted, one has to have some pation , wait until all finished.

And then try to make one task at a time only.

Particularly when also ntfs partitions are involved, do not combine such task with others.

---

