---
title: "Change directory to a usb device"
date: 2011-01-20
forum: General Help
---

### Post by ranger_cole on 2011-01-20
I want to change directories in the terminal to a mounted usb device.

---

### Post by reobedr on 2011-01-20
cd /media/name of USB/

---

### Post by reobedr on 2011-01-20
Ignore

---

### Post by reobedr on 2011-01-20
:oops:

---

### Post by pqwoerituytrueiwoq on 2011-01-20
you could use a symbolic link 
```
man ln
```

---

### Post by ranger_cole on 2011-01-20
jaypugh@jaypugh-desktop:~$ cd/media/PENDRIVE/
bash: cd/media/PENDRIVE/: No such file or directory

---

### Post by reobedr on 2011-01-20
you need a space between cd and /media/

---

### Post by pqwoerituytrueiwoq on 2011-01-20
> **ranger_cole said:**
> jaypugh@jaypugh-desktop:~$ cd/media/PENDRIVE/
bash: cd/media/PENDRIVE/: No such file or directory

```
cd /media
ls
cd "My Ipod"
```ls will tell you every item in the current directory

"My Ipod" is an example
[IMG]http://i52.tinypic.com/2iid2kj.png[/IMG]

@ my 1st post 
was thinking you wanted to change the location drives are mounted to via terminal

*anyone know why the forums are being a pain? i am blaming the database server*

---

### Post by reobedr on 2011-01-20
ot: > *anyone know why the forums are being a pain? i am blaming the database server*

[http://ubuntuforums.org/announcement.php?f=331](http://ubuntuforums.org/announcement.php?f=331)

---

### Post by ranger_cole on 2011-01-20
I have changed directories to usb per the instructions.  Thanks for the quick response.:)

---

### Post by ranger_cole on 2011-01-20
I have changed directories to usb per the instructions.  Thanks for the quick response.:)

---

### Post by Advice Pro on 2011-03-14
How about from ```
/media
``` In my situation, [Troubleshooting Ubuntu 9.10!](http://ubuntuforums.org/showthread.php?t=1704526), I can't access my usb devices stored there.  Please suggest an alternate directory for me store change them to.

---

