---
title: "Compiling programs | Install previously compiled"
date: 2010-06-28
forum: General Help
---

### Post by specialalaa on 2010-06-28
Hi. I didn't know where to post this, so I just posted it here..

I compiled and installed ALSA 1.0.23 on Ubuntu using the following steps:
```
1. sudo apt-get build-essential
2. wget ftp://ftp.alsa-project.org/pub/drive...1.0.23.tar.bz2
3. tar -xjf alsa-driver-1.0.23.tar.bz2
4. cd alsa-driver-1.0.23/
5. ./configure
6. make
7. sudo make install
8. alsamixer (don't know if this step was necessary since my volume was already enabled)
9. reboot
```
Now, **I want to install it again** (because I installed PAE afterwards, which installed a linux image with PAE enabled, but it didn't have alsamixer 1.0.23).. So do I have to start all over again (from step 4), or can I start from step 7? (of course I'll have to cd to alsa-driver-1.0.23 first).. Thanks

---

