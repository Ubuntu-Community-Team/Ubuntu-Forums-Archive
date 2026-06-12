---
title: "how to get modern ubuntu to run on old arch (i586)"
date: 2012-05-03
forum: General Help
---

### Post by jimmikaelkael on 2012-05-03
Hi,

I have some embedded device that is using a Vortex86MX CPU (at 1GHz), it have 1 GB of RAM so it should be sufficient to run Lubuntu 12.04 LTS (it currently runs Ubuntu 9.04).

Unfortunately, Canonical dropped support for i586 processors till version 10.10 (from both kernel and gcc build it seems). As a result the new Lubuntu 12.04 LiveCD won't start on this machine. The problem is that this processor is lacking the cmov instruction support.

I'd like to know which steps I will need to ba able to run modern ubuntu on this processor.
I'm aware I will need to recompile the kernel changing the config to support i586 processor family.
But I guess I need too to recompile GCC and so all the packages I'm using, right ?

I will do the whole needed rebuild on a stronger i686 as host, using Lubuntu 12.04, but what I really don't know is where to start... Do I need to rebuild a new GCC targetting i586 on the host before to rebuild the kernel ? Or should it be the kernel first, then GCC, etc...
I'm really lacking some knowledge on how to achieve this so any help will be appreciated.

Thank you.

---

### Post by evilmoo on 2012-11-18
I would like to know this as well.  I realize it would be a long and involved process but would like information on how to do it regardless.

Thanks!

---

### Post by Yellow Pasque on 2012-11-18
Use Debian...

---

### Post by idoitprone on 2012-11-18
New ubuntu version require sse instructions. Use debian  as Temujin suggest

[http://www.debian.org/CD/torrent-cd/](http://www.debian.org/CD/torrent-cd/)

they target i386

---

### Post by rnerwein on 2012-11-19
> **idoitprone said:**
> New ubuntu version require sse instructions. Use debian  as Temujin suggest

[http://www.debian.org/CD/torrent-cd/](http://www.debian.org/CD/torrent-cd/)

they target i386
may be this link will help you

[http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present)

good luck

---

### Post by jimmikaelkael on 2012-12-02
I will suggest what the others are suggesting :)

On my side, I ended up using debian-testing-i386-xfce+lxde cdimage on this machine and this is really perfect as I really needed a lightweight system.

I just had a problem to compile with default gcc install (4.6) ending with illegal instruction... But I installed gcc-4.5 and all is good.

---

