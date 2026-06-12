---
title: "Downgrading Compiz in Ubuntu 11.10?"
date: 2011-12-12
forum: General Help
---

### Post by cwklinuxguy on 2011-12-12
Hello. I have found instructions for downgrading Compiz in Ubuntu 11.04 to an older version not affected by the Unity implimentation that causes it to break (and of course doing so causes Unity to break, which is OK being that I am using Ubuntu solely in the building of my new distro). However, the instructions I found for Ubuntu 11.04 do not work in 11.10...I assume the names of some packages have been changed in the upgrade process. Does anybody know how to do this in 11.10?

---

### Post by oldtimer7777 on 2011-12-12
> **cwklinuxguy said:**
> Hello. I have found instructions for downgrading Compiz in Ubuntu 11.04 to an older version not affected by the Unity implimentation that causes it to break (and of course doing so causes Unity to break, which is OK being that I am using Ubuntu solely in the building of my new distro). However, the instructions I found for Ubuntu 11.04 do not work in 11.10...I assume the names of some packages have been changed in the upgrade process. Does anybody know how to do this in 11.10?

I just don't use compiz in Ubuntu 11.10..  I tried it, and it didn't work the way it did in 11.04, so I rolled everything back to Ubuntu 11.04. That is as good as it gets for now. Sometimes it works, and sometimes it breaks everything.  It isn't really worth the hassle for window dressing.

---

### Post by longgay on 2012-03-10
> **cwklinuxguy said:**
> Hello. I have found instructions for downgrading Compiz in Ubuntu 11.04 to an older version not affected by the Unity implimentation that causes it to break (and of course doing so causes Unity to break, which is OK being that I am using Ubuntu solely in the building of my new distro). However, the instructions I found for Ubuntu 11.04 do not work in 11.10...I assume the names of some packages have been changed in the upgrade process. Does anybody know how to do this in 11.10?

It's a repo from [http://www.opencompositing.ru/](http://www.opencompositing.ru/) for ubuntu 11.04 but it works for ubuntu 11.10. This repo contains motified compiz 0.8.8. Besides that you have to add **debian stable repo** too.

First, you have to remove compiz 0.9.x and all dependencies:

sudo apt-get purge compiz compiz-plugins-unsupported compiz-plugins-extra compiz-plugins-main compiz-plugins compizconfig-settings-manager libcompizconfig0 compizconfig-python
sudo apt-get purge emerald (If it's installed)

Add new compiz repo and debian stable repo use "Software sources"

deb [http://www.opencompositing.ru/uploads/ubuntu](http://www.opencompositing.ru/uploads/ubuntu) natty main backports
deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze main
and run
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4FBAC7BD
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 473041FA
sudo apt-get update

You should install emerald at the same time too.
Done! Just install new compiz and enjoy!!!:popcorn:
I've done it in my Linuxmint 12 mate.

Sorry for my english. I'm not a English user.

I have a  question: how to insert image in this forum????

---

