---
title: "locked out after updates"
date: 2009-11-11
forum: General Help
---

### Post by swaddo on 2009-11-11
ok, this is a weird one. it's not just an "I've forgotten my password" issue

i installed Jaunty on a new machine yesterday, applied all updates, installed dtc-toaster and configured it ... all good so far. This morning i thought i'd do a dist-upgrade and installed the git version of dtc (from deb packages that I built) and now i cannot log in to the machine at all.

su, sudo, and std console/gdm logins all respond with Auth Failed messages

so I've booted to the live cd, mounted and chrooted to the installation and done the following (password was reset to "abc")

```

ubuntu@ubuntu:~$ cat /etc/issue.net
Ubuntu 9.04
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: clean, 173946/60440576 files, 5087500/241734063 blocks
ubuntu@ubuntu:~$ sudo mkdir /mnt/karmic
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/karmic/
ubuntu@ubuntu:~$ sudo chroot /mnt/karmic/
root@ubuntu:/# cat /etc/issue.net
Ubuntu 9.10
root@ubuntu:/etc/init.d# passwd blake
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
root@ubuntu:/etc/init.d# su - blake
blake@ubuntu:~$ sudo -i
sudo: unable to resolve host ubuntu
[sudo] password for blake: 
Sorry, try again.
[sudo] password for blake:

```

Anyone got any ideas where to look for the cause of this?

---

### Post by bashphoenux on 2009-11-11
when you login does it say wrong username/password ??

---

### Post by swaddo on 2009-11-11
It is saying Authentication failure

i'm wondering now if something got borked in PAM? Havent had to mess with it yet so this could end badly :)

---

### Post by swaddo on 2009-11-11
gah, if I close the terminal after doing the chroot i cant run anything at all!!

clean install time ...

---

### Post by bashphoenux on 2009-11-11
lol then clean install it has to be :)

---

### Post by swaddo on 2009-11-12
it has just happened again only this time there no updates immediately before the failure. Updates were done first thing this morning and I noticed that libpam-unix2 was included ... i suspect this guy is the culprit.

Anyway, everything was just dandy then i went out to lunch and now ... 

```
blake@www1:~$ sudo -i
[sudo] password for blake: 
Sorry, try again.
[sudo] password for blake: 
```auth log included below shows the results when I tried to "sudo -i" and ssh from my notebook (10.0.0.100)

```

Nov 13 12:56:20 www1 sudo: pam_unix2(sudo:auth): conversation failed
Nov 13 12:56:20 www1 sudo:    blake : 2 incorrect password attempts ; TTY=pts/0 ; PWD=/home/blake/Projects/dtc ; USER=root ; COMMAND=/bin/bash

```

---

### Post by swaddo on 2009-11-12
[LEFT]ok, this is completely down to libpam-unix2. installing it alone is sufficient to bork all authentication. since this was a dependency of the other package it silently did its thing:o
[/LEFT]

---

