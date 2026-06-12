---
title: "In boot &quot;error occurred while mounting&quot;"
date: 2011-01-16
forum: General Help
---

### Post by 8301 on 2011-01-16
As it says...

While booting Ubuntu an mounting error appears occasionally.

"An error occurred while mounting /home/htpc/HTPC 4"
Press S to skip press M for manual

So when try the manual way

```
htpc@htpc ~ $ sudo mount /dev/sda1 /home/htpc/HTPC\0404
/dev/sda1 looks like swapspace - not mounted
mount: you must specify the filesystem type

```

Then I check my fstab

```
/dev/sdc1	/home/htpc/HTPC\0401	ext4	users,rw	0	0
/dev/sdd1	/home/htpc/HTPC\0402	ext4	users,rw	0	0
/dev/sde1	/home/htpc/HTPC\0403	ext4	users,rw	0	0
/dev/sda1	/home/htpc/HTPC\0404	ext4	users,rw	0	0

```

I have not experienced this problem with my other drives only on  /dev/sda1	/home/htpc/HTPC\0404

---

### Post by 8301 on 2011-01-16
bump

---

### Post by 8301 on 2011-01-18
bump

---

