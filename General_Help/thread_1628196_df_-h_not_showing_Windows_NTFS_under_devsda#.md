---
title: "df -h not showing Windows NTFS under /dev/sda#"
date: 2010-11-22
forum: General Help
---

### Post by jehiva on 2010-11-22
Hello all,

How do I force Ubuntu to see my Windows NTFS partition when typing ```
df -h
```?

I have freshly installed Win7 and Ubuntu 10.10 and it is not automatically discovering the partition (previously with Win7 / Ubuntu 10.04 it did).

Is there a file I can manually edit, or a command to run?

---

### Post by Verbeck on 2010-11-22
have you got it mounted before running that command?

---

### Post by jehiva on 2010-11-22
Hi Verbeck, I am unable to see the file system when clicking on Places.  

How would I go about mounting it manually?

---

### Post by Verbeck on 2010-11-22
do you see it when you run
```
sudo fdisk -l
``` or ```
sudo blkid -c /dev/null
```

edit: post the output here if you're unsure

---

### Post by jehiva on 2010-11-23
Hello Verbeck,

Turned out it wasn't mounted /facepalm.

Issue resolved, thanks for the help.

---

