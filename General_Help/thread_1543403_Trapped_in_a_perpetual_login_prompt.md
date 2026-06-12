---
title: "Trapped in a perpetual login prompt"
date: 2010-08-01
forum: General Help
---

### Post by missingno on 2010-08-01
After my wireless had recently broken without having made any changes to my system and I tried many different things to try and fix it with no success, I decided to reinstall 10.04. But after doing so, I came upon a crippling new problem.

After logging in, the screen just turned black with a blinking cursor for a moment and then the login prompt came up again. I figured maybe the installation disc I burned didn't come out right, so I burned another and made sure to use its utility to check integrity. It said the disc was fine, I reinstalled, same problem remained. I tried failsafe X, but that didn't work either.

EDIT: Looks like I can open GNOME by dropping into the recovery terminal as root and then opening X, so I could log in as root but not as my account. There must be some setting in my home folder that it didn't like - I'm now restoring all my old package markings in Synaptic and upgrading everything. Hopefully that'll make this issue go away.

EDIT2: Alright, that didn't fix it, but I found that recovery mode -> root shell -> su [username] -> startx works just fine so I can get in with this wonky workaround. But I'd still like to have the login prompt itself fixed.

Also this isn't really the place to bring this up, but when becoming root from recovery mode it never asked me for a password or anything. That's really not good!

---

### Post by dino99 on 2010-08-01
edit the boot line and add: rw init=/bin/bash


[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

---

### Post by missingno on 2010-08-01
Where's the boot line?

---

