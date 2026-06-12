---
title: "File permissions"
date: 2011-05-22
forum: General Help
---

### Post by abdulq8 on 2011-05-22
Hello guys, I have a public folder on a web server and I would like to make any file in that folder have the 655 permission once its created

Thanks in advance,
Abdul

---

### Post by ericzmeh on 2011-05-22
I believe if you make the directory 655 using

```

sudo chmod -r 655

```
This will make all files and folders the same.
Is that what you want to do?

---

### Post by abdulq8 on 2011-05-22
> **ericzmeh said:**
> I believe if you make the directory 655 using

```

sudo chmod -r 655

```
This will make all files and folders the same.
Is that what you want to do?

didn't work

---

### Post by ericzmeh on 2011-05-22
Can you post your input/output?

---

### Post by abdulq8 on 2011-05-22
> **ericzmeh said:**
> Can you post your input/output?

```
> chmod -r 655 script/
chmod: cannot access `655': No such file or directory
chmod: script/: new permissions are -wxr-xr-x, not -wx--x--x

```

---

### Post by ericzmeh on 2011-05-22
You need to run chmod as root.  See:
```

man chmod

```

And i'm not sure that the dir name should have a "/" after it, but not for certain.

---

### Post by abdulq8 on 2011-05-22
I am not the root on the server. This is the university server that I have some codes I want to share with others

---

### Post by ericzmeh on 2011-05-22
You cannot change the permission bits of any file or folder without being root or issuing the "sudo" command from what I understand.  You may need to talk to the university about creating a sudo account for you.

---

### Post by abdulq8 on 2011-05-22
```
> mkdir test
> ll
total 32
drwxr-xr-x 3 aalotaib student 1024 2011-05-22 19:48 .
drwxr-xr-x 5 aalotaib student 1024 2011-05-22 19:06 ..
-rwxr-xr-x 1 aalotaib student   22 2011-05-22 19:07 one.pl
drwx------ 2 aalotaib student   80 2011-05-22 19:48 test
-rw------- 1 aalotaib student   14 2011-05-22 19:32 two.py
> chmod 777 test/
> ll
total 32
drwxr-xr-x 3 aalotaib student 1024 2011-05-22 19:48 .
drwxr-xr-x 5 aalotaib student 1024 2011-05-22 19:06 ..
-rwxr-xr-x 1 aalotaib student   22 2011-05-22 19:07 one.pl
drwxrwxrwx 2 aalotaib student   80 2011-05-22 19:48 test
-rw------- 1 aalotaib student   14 2011-05-22 19:32 two.py

```

---

### Post by abdulq8 on 2011-05-22
can anyone help me?

---

### Post by linuxinstalledfromhdd on 2011-05-22
Are you the administrator for this system?  If not, that is who you would need to contact about this situation.

---

