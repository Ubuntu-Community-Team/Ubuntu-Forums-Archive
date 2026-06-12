---
title: "libgtk2.0-dev dependency problems"
date: 2006-06-12
forum: General Help
---

### Post by loftx on 2006-06-12
Hi All, I just wiped my root partition and reinstalled Dapper and ran into some dependancy problems. 

I Tried to installed some developement packages and found the problem was with libglib2.0 as when I tried to install libglib2.0-dev

```
libglib2.0-dev:
  Depends: libglib2.0-0 (=2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed
```

I hadn't done anything to the system except install a few packages and run easyubuntu and make a few changes in grub/fstab.

I fixed the problem (hopefully) by grabbing the latest libglib2.0-dev from launchpad which was 2.10.3-0ubuntu1, though somehow apt-get didn't see this and dpkg complained about using a package later than the repos.

I had run apt-get update and upgrade but it didn't seem to help - anyone know what might have been the problems?

---

### Post by xen on 2006-06-14
Hey, i'm having the same troubles, I need this so I can compile some beep-media-player plugins!

---

### Post by Hebus95 on 2006-06-21
Same problem. It prevents me from programming in GTK+ :( 

```
Les paquets suivants contiennent des dépendances non satisfaites :
  libgtk2.0-dev: Dépend: libpango1.0-dev (>= 1.10.0-2) mais ne sera pas installé                 Dépend: libcairo2-dev mais ne sera pas installé
                 Dépend: libxcursor-dev mais ne sera pas installé
                 Dépend: libxfixes-dev mais ne sera pas installé
E: Paquets défectueux
```

---

### Post by Hebus95 on 2006-06-21
Try this, it worked for me : :p 

```
sudo **aptitude** install  gnome-core-devel
```

Aptitude will detect some broken packages and then will do the job.

It fails with apt-get however. Why ??

---

