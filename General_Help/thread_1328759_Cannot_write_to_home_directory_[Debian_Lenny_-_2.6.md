---
title: "Cannot write to home directory [Debian Lenny - 2.6.26-2-686]"
date: 2009-11-16
forum: General Help
---

### Post by Bu7753x on 2009-11-16
I can read anything from my home directory, but cannot write anything to it.  Any idea on what's wrong?

```
buttsex@comp2:~$ mkdir a
mkdir: cannot create directory `a': Permission denied
buttsex@comp2:~$ echo a >> a.txt
bash: a.txt: Permission denied
buttsex@comp2:~$ su
Password: 
comp2:/home/buttsex# echo a >> a.txt
comp2:/home/buttsex# cat a.txt
a
```A demonstration of what's wrong.  As you can see, everything works as root, but I'm (understandably) a bit hesitant to do everything as a superuser.

---

### Post by lruc on 2009-11-16
Haha buttsex. There's the problem.

---

### Post by Bu7753x on 2009-11-16
> **lruc said:**
> Haha buttsex. There's the problem.
Pretty sure that isn't it.

---

### Post by Iowan on 2009-11-16
Check permissions to see who actually owns the directory - if it's **root**...

---

### Post by Bu7753x on 2009-11-16
> **Iowan said:**
> Check permissions to see who actually owns the directory - if it's **root**...
```
buttsex@comp2:~$ ls -l /home
total 4
drwxr-xr-x 81 root root 4096 2009-11-16 18:11 buttsex
buttsex@comp2:~$ sudo chown buttsex /home/buttsex
sudo: unable to resolve host comp2
[sudo] password for buttsex: 
buttsex@comp2:~$ echo a >> a.txt
bash: a.txt: Permission denied
buttsex@comp2:~$ ls -l /home
total 4
drwxr-xr-x 81 buttsex root 4096 2009-11-16 18:11 buttsex

```

Edit:
```
buttsex@comp2:~$ sudo chown -R buttsex /home/buttsex

```
solved it.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
```
man chown
``` will show you how to change the permissions back to buttsex rather than root. I think it's ```
sudo chown -R buttsex /home
``` but I would look at the man page first. You will also have to change read/write permissions. If you want both it's ```
chmod 777 -R /home
```

Edit: Beat me to it...

---

