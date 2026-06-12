---
title: "recursively changed permissions.  HELP!"
date: 2010-05-23
forum: General Help
---

### Post by wolfv6 on 2010-05-23
I did a clean install from Ubuntu 09.04 to 10.04 and restored my files from tar.
Everything worked fine until I tried my weekly rsync backup.
The permissions seemed to be causing problems, so I recursively changed all the permissions in my home directory:
```
~/Documents$ sudo chmod -R 644 /home/wolf/
[sudo] password for wolf: 
chmod: cannot access `/home/wolf/.gvfs': Permission denied
```So now all the directories and files have read permission for everyone:
```
~/Documents$ ls -A
ls: cannot open directory .: Permission denied
~/Documents$ sudo ls -lA
[sudo] password for wolf: 
total 80
drw-r--r--  2 wolf wolf  4096 2010-05-22 20:45 career
drw-r--r-- 23 wolf wolf  4096 2010-05-02 17:17 computer_languages
drw-r--r--  2 wolf wolf  4096 2009-08-09 23:29 .ecryptfs
drw-r--r-- 21 wolf wolf  4096 2010-05-02 17:23 misc
-rw-r--r--  1 wolf wolf 27298 2010-05-23 13:01 next.odt
drw-r--r--  3 wolf wolf  4096 2010-05-23 15:46 PC_maintenance
drw-r--r--  5 wolf wolf  4096 2010-05-08 01:43 software_projects
```Now I can't even look at my own directory:
```
/home$ cd /home/
/home$ ls -lA
total 20
drwx------  2 root root 16384 2010-05-07 01:01 lost+found
drw-r--r-- 42 wolf wolf  4096 2010-05-23 15:35 wolf
/home$ cd /home/wolf
bash: cd: /home/wolf: Permission denied
/home$ sudo cd /home/wolf
[sudo] password for wolf: 
sudo: cd: command not found
/home$
```:confused:  
Your help is much appreciated.

---

### Post by albinootje on 2010-05-23
Do this :
```

sudo bash
/usr/bin/find /home/wolf/ -type f -exec chmod 644 {} \;
/usr/bin/find /home/wolf/ -type d -exec chmod 755 {} \;
exit

```

That should fix most of it, but check your settings for e.g. ~/.gnupg/

---

### Post by wolfv6 on 2010-05-23
> **albinootje said:**
> Do this :
```

sudo bash
/usr/bin/find /home/wolf/ -type f -exec chmod 644 {} \;
/usr/bin/find /home/wolf/ -type d -exec chmod 755 {} \;
exit

```That should fix most of it, but check your settings for e.g. ~/.gnupg/

I understand some of this.  I read somewhere that a directory's * executable bit* is needed to open  the directory.  I guess "f" is for file and "d" is for directory.  "find -type d -exec chmod 755" finds all the directories and sets their  * executable bit*s.

This worked:
```
~$ echo $SHELL
/bin/bash
~$ sudo /usr/bin/find /home/wolf/ -type d -exec chmod 755 {} \;
[sudo] password for wolf: 
/usr/bin/find: `/home/wolf/.gvfs': Permission denied

```Thank you so much.  You just saved my weekend:).

---

