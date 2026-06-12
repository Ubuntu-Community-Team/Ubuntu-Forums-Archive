---
title: "drwxrwxrw-, but still get &quot;permission denied&quot;"
date: 2010-06-07
forum: General Help
---

### Post by calicoAngelina on 2010-06-07
Hi,

I'm trying to install RANCID on 10.04 LTS server.

I had a successful apt-get of the package, and have seemed to have success up to the current point where I need to enter router IP addresses in the router.db files.

However, I can't "cd" into the directories where I believe the router.db files are supposed to be.

In /etc/rancid/rancid.conf, I have BASEDIR=/var/lib/rancid, so that's where I seem to be reading the router.db directories should be.


"ls -l" in /var/lib/rancid gives:
drwxrwxrw- 4 rancid rancid 4096 2010-05-25 18:48 Alameda
drwxr-x--- 4 rancid rancid 4096 2010-05-25 18:48 BCC
drwxr-x--- 4 rancid rancid 4096 2010-05-25 18:48 District
drwxr-x--- 4 rancid rancid 4096 2010-05-25 18:48 Laney
drwxr-x--- 4 rancid rancid 4096 2010-05-25 18:48 Merritt

(Alameda has different permissions because I've been trying to get this to work.  The other have the permissions they got from being created by the program.)

(The followingis true for all the directories, not just for the example, Alameda.)

If I "cd Alameda", I get:
-bash: cd: Alameda: Permission denied

If I "sudo cd Alameda", or "sudo -u rancid cd Alameda", I get:
sudo: cd: command not found

If I "ls -l Alameda", I get:
linnea@friesian:/var/lib/rancid$ ls -l Alameda
ls: cannot access Alameda/CVS: Permission denied
ls: cannot access Alameda/routers.up: Permission denied
ls: cannot access Alameda/router.db: Permission denied
ls: cannot access Alameda/configs: Permission denied
ls: cannot access Alameda/routers.down: Permission denied
ls: cannot access Alameda/routers.all: Permission denied
total 0
d????????? ? ? ? ?                ? configs
d????????? ? ? ? ?                ? CVS
-????????? ? ? ? ?                ? router.db
-????????? ? ? ? ?                ? routers.all
-????????? ? ? ? ?                ? routers.down
-????????? ? ? ? ?                ? routers.up

If I do "vi Alameda/routers.db", I get a screen, and I can type, but when I try to save, I get:
"Alameda/routers.db" E212: Can't open file for writing


Anyone, help?

Linnea

---

### Post by Serpher on 2010-06-07
Use the command:

```
sudo -i
```

Then try doing your tasks normally.

---

### Post by calicoAngelina on 2010-06-08
> **Serpher said:**
> Use the command:

```
sudo -i
```

Then try doing your tasks normally.


Yes, thanks, that did it.

---

