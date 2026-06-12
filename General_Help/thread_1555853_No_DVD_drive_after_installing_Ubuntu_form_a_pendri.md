---
title: "No DVD drive after installing Ubuntu form a pendrive"
date: 2010-08-18
forum: General Help
---

### Post by andy_blah on 2010-08-18
I knew that there was a guide around fixing this issue. After I install Ubuntu from a pendrive readied by unetbootin, I am unable to use the DVD drive that I have, that also works fine under Windows XP. I've tried searching around for that same guide but as usual the search function gives me bogus results.

---

### Post by andy_blah on 2010-08-19
*bump* Anyone?

---

### Post by andy_blah on 2010-08-19
Nevermind, I went on to modify the fstab file. Since nobody wanted/noticed to help I'll post in what i did to fix this issue.
First you must create a directory named 'cdrom' in /media/

```
sudo mkdir /media/cdrom
```

And after that edit fstab

```
sudo gedit /etc/fstab
```

Then past this at the end of the file and save:

```
/dev/cdrom      /media/cdrom   iso9660 ro	user	noauto	0	0
```

---

