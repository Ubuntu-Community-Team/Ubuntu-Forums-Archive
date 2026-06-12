---
title: "Trying To Get Nvidia Dual Displays Functional"
date: 2010-05-19
forum: General Help
---

### Post by formengr on 2010-05-19
i'm pretty noobish w/ubuntu though have been using it for about 6 months or so. i just installed lucid lynx last weekend (reinstalled it and my w7 os a few times actually after the upgrade from 9.xx to 10.04 went horribly awry).

can anyone help me to get my dual monitors working? i have a PNY NVIDIA Quadro FX 380 low profile card which has dual monitor support and am trying to get my dual displays set up but when i go pref>admin>nvidia xserver settings, this gives me the following msg:
> you do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
so i opened a terminal and did this:
> sudo nvidia-xconfig
which tells me:
> Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

i then restart ubuntu (that's what i'm supposed to do to"restart the X server", right?) and i get a startup error that wants to put me in low graphics mode, but actually ends up not in low graphics when i start.

much appreciation in advance. :)

---

### Post by formengr on 2010-05-19
bump. help? anyone?  :)

---

### Post by SlidingHorn on 2010-05-19
Not to be the bump nazi or anything, but there are a lot of posts to cover.  Try to give it some time before bumping your thread

---

### Post by formengr on 2010-05-19
got it working. not really sure how exactly. if/when it decides not to work, it would be cool if someone could chime in and offer some guidance or opinion.  thanks!

---

### Post by formengr on 2010-05-20
and of course a few more reboots and i'm back to the original error message and a solo monitor. any guidance is appreciated. thanks.

---

