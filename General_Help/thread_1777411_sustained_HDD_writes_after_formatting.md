---
title: "sustained HDD writes after formatting"
date: 2011-06-07
forum: General Help
---

### Post by fraktalek on 2011-06-07
Hi,

I'm seeing sustained disk writes of about 2 MB/s in the indicator-multiload indicator in Unity. I determined that it is writes on my 500GB HDD on /dev/sdb. This behaviour started after I used Gparted to create a single 500GB ext4 partition and also selected that it should be formatted to ext4 in Gparted.

Is this usual? It also survived a reboot.. I assume that it is the full formatting taking place in the background?

I saw no activity using pidstat or iotop. Only using vmstat -d revealed the writes.

---

### Post by Mark Phelps on 2011-06-08
The Ext4 filesystem is a journaling filesystem -- so it routines writes to the filesystem in the background.

Is this what is concerning you?

---

### Post by psusi on 2011-06-08
Yes, mke2fs in 11.04 now defaults to a quick format and it is finished in the background.

---

### Post by fraktalek on 2011-06-08
Thanks, I was just wondering as it was slightly unexpected for me.

---

