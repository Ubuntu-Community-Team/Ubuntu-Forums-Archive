---
title: "remastersys gives small iso file"
date: 2009-12-24
forum: General Help
---

### Post by s263030 on 2009-12-24
Hi everyone

I'm trying to make DVD live from my current Ubuntu 9.10 with remastersys 

using this command 

```
sudo remastersys dist
```

at the end i end-up having small iso ( 34 kb ) file with punch of other folders and files 

```
-rw-r--r--  1 root root   34K 2009-12-25 00:28 custombackup.iso
-rw-r--r--  1 root root    81 2009-12-25 00:28 custombackup.iso.md5
drwxr-xr-x 10 root root  4.0K 2009-12-25 00:07 dummysys
drwxr-xr-x  4 root root  4.0K 2009-12-25 00:28 ISOTMP
-rw-r--r--  1 root root 1002K 2009-12-25 00:28 remastersys.log
-rw-r--r--  1 root root  2.7K 2009-12-25 00:07 varexc
-rw-r--r--  1 root root  3.3K 2009-12-25 00:07 varexc.tmp
```

Any idea ?

best regards

---

### Post by s263030 on 2009-12-24
up up

It's urgent .. help me plz

---

### Post by bodhi.zazen on 2009-12-25
look in the log file and see if there are any errors.

Otherwise, clean and then re-run.

---

