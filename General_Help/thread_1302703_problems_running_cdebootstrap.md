---
title: "problems running cdebootstrap"
date: 2009-10-27
forum: General Help
---

### Post by itchy8me on 2009-10-27
hey guys,

i'm trying to bootstrap a debian system with the command:
```
cdebootstrap --arch=arm --foreign --include locales,openssh-server,screen,udev etch /root/blackstone_chroot http://ftp.nl.debian.org/debian
```
however the build just hangs at:
```
P: Retrieving Release
```
and does nothing else.

has anyone else had similar problems, know a solution or see that i'm doing something wrong?
my system is karmic 64 bit

thanks

---

