---
title: "file permission problem"
date: 2009-07-06
forum: General Help
---

### Post by firsttimeuser on 2009-07-06
I have mysql running which automatically exports some data from its table to file 'mysqltop' under /tmp/ every 5 minutes.

bill@dao:~$ ls -tl /tmp/
total 932
-rw-rw-rw- 1 mysql mysql 188687 2009-07-06 16:33 mysqltop

the problem is, i can not use script which runs as "bill" to delete this file, the user is already in mysql group.

bill@dao:~$ id
uid=1000(bill) gid=1000(bill) groups=0(root),4(adm),20(dialout),24(cdrom),46(plugdev),110(lpadmin),111(sambashare),112(admin),113(mysql),1000(bill)

bill@dao:~$ rm /tmp/mysqltop
rm: cannot remove `/tmp/mysqltop': Operation not permitted

so without "sudo mysql", what else can I do to make the file deleteable by user bill?

thanks!

---

### Post by LowSky on 2009-07-06
you could move the temp file to your home folder, then you wont need root access.

---

### Post by firsttimeuser on 2009-07-06
the problem is mysql cannot access my home dir

---

