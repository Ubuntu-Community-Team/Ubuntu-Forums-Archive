---
title: "Installing mod_perl for apache2"
date: 2009-08-24
forum: General Help
---

### Post by gordonsowner on 2009-08-24
Hi,

Is there a way via 'aptitude' to install mod_perl for my apache2 webserver, or do I have to compile and such from scratch mod_perl and hand-configure it's use in apache2 (and, if that is the case, though it's not an Ubuntu question, could anybody direct me to info on how to do that?).

tia,
Matt

---

### Post by unutbu on 2009-08-24
Based on the output of 
```
apt-cache search mod-perl
```
I'm guessing
```
sudo aptitude install libapache2-mod-perl2
```
is what you want.

---

### Post by gordonsowner on 2009-08-24
Thank you!

---

### Post by ITfromScratch on 2013-04-18
> **unutbu said:**
> Based on the output of 
```
apt-cache search mod-perl
```
I'm guessing
```
sudo aptitude install libapache2-mod-perl2
```
is what you want.

Thank you.

It's funny that after all this time the package name is the same. I did the cache search just to be sure, but it hasn't changed.

Also, this is the first time I've installed an Apache mod through aptitude. I've got to say, it's a slick way to do it. It appears that the module was enabled in the installation process as well, so running the install command is all you need to get up and running with mod_perl.

---

### Post by oldos2er on 2013-04-18
Closed, please don't bump old threads.

---

