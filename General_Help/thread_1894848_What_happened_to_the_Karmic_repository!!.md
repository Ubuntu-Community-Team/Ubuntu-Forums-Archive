---
title: "What happened to the Karmic repository??!!"
date: 2011-12-13
forum: General Help
---

### Post by scotausborn on 2011-12-13
[http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)

Why is Karmic Koala no longer listed with the other maintained distros?  I needed to install some packages on our server this morning, and discovered than none of karmic archives are found when running apt-get.

---

### Post by BC59 on 2011-12-13
Karmic is no longer supported. Try to upgrade to newer version.

---

### Post by coffeecat on 2011-12-13
Because Karmic has been end-of-life since April. If you want to install some packages or update your system to the last set of updates, you can use the old-releases repository:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Which you'll need for upgrading your present system anyway.

Time to upgrade to 10.04 or fresh install. There have been no security patches for Karmic since April.

---

### Post by Erik1984 on 2011-12-13
Karmic is no longer supported. However you probably can still install stuff from the old-releases repository. I did that successfully with the Gutsy repos.

[http://www.prash-babu.com/2011/02/get-repositories-for-no-longer.html](http://www.prash-babu.com/2011/02/get-repositories-for-no-longer.html)

---

### Post by oldtimer7777 on 2011-12-13
9.10 is not at EOL (END OF LIFE)

Ubuntu doesn't support it anymore. You waited too long to upgrade your system.  Now you need to do a fresh install:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **scotausborn said:**
> [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)

Why is Karmic Koala no longer listed with the other maintained distros?  I needed to install some packages on our server this morning, and discovered than none of karmic archives are found when running apt-get.

---

### Post by Habitual on 2011-12-13
```
cp /etc/apt/sources.list /etc/apt/sources.list.org
vi /etc/apt/sources.list 
```and remove all lines and add:

## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

Save and exit.

apt-get update
apt-get install <package>

---

### Post by scotausborn on 2011-12-14
Thank you so much!  We're running VMWare Server on a patched kernel, so  upgrading is a serious adventure.  Now I can install phpmyadmin without  going through all of that... thanks again.

---

### Post by Habitual on 2011-12-14
Glad it worked out!

---

### Post by mlentink on 2011-12-14
> **scotausborn said:**
> Thank you so much!  We're running VMWare Server on a patched kernel, so  upgrading is a serious adventure.  Now I can install phpmyadmin without  going through all of that... thanks again.

If you should decide to upgrade, you might want to do so to a LTS release. The current one is Ubuntu 10.04 (Lucid Lynx), and the next one will be Ubuntu 12.04 (Precise Pangolin). LTS-releases are supported for a much longer period than normal releases, so I think that would suit your needs much better.

See: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

