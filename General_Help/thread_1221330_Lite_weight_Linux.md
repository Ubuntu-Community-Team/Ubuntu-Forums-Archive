---
title: "Lite weight Linux?"
date: 2009-07-23
forum: General Help
---

### Post by Kal318 on 2009-07-23
Any one know if there's a lite weight version of linux. Specifically I need to run only the Elisa Media Center. The less of all the bells and whistles of most version of linux the better.

---

### Post by kerry_s on 2009-07-23
just do a base install & add only what you want.

---

### Post by moore.bryan on 2009-07-23
debian, neat.

---

### Post by kerry_s on 2009-07-23
yeah debian works great. just grab the net installer:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

64bit: [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/iso-cd/)

at the package selection just unselect desktop & standard to get a base install. then just apt-get what you want.
example:

apt-get install xorg elisa

setup auto log in and have it launch elisa or does elisa need a window manager to run?

---

### Post by darolu on 2009-07-23
Deli Linux is one of the lightest distros out there, it runs on 486 machines with 16MB of RAM: [http://www.delilinux.de/](http://www.delilinux.de/)

Damn Small Linux is also very light (and only 50MB!): [http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)

If the computer you are going to install it is not THAT old/slow, you can try Xubuntu: [http://www.xubuntu.org](http://www.xubuntu.org)

Slackware is not "light" but it is very efficient, it uses XFCE too: [http://www.slackware.com](http://www.slackware.com)

---

### Post by Kal318 on 2009-07-25
Thanks all. this is exactly the information I was looking for. :)

---

