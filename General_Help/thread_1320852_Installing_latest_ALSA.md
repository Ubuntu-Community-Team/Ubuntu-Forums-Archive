---
title: "Installing latest ALSA"
date: 2009-11-09
forum: General Help
---

### Post by cothrige on 2009-11-09
I recently purchased a new laptop, HP Pavilion dv6-1355dx, and installed Ubuntu 9.10 64bit on it.  Just about everything worked just as expected with the exception of the headphone jack, which did not mute the speakers.  In order to fix this, and thanks to the many informative posts at this forum, I finally decided to follow the instructions at [http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/) and upgrade to the latest alsa.  I then added "options snd-hda-intel model=dell-m4-1" to the bottom of /etc/modprobe.d/alsa-base.conf.  This solved my problem.

However, being entirely new to Ubuntu I am now wondering how to best proceed.  It wasn't too much trouble compiling the software, but obviously it would be best if I could avoid doing it over again later.  With that in mind, what might I need to do now in order to avoid any conflicts with future software updates?

---

