---
title: "&quot;X -config&quot; doesn't work"
date: 2006-05-08
forum: General Help
---

### Post by bobpaul on 2006-05-08
I've been using ```
X :1 -config xorg.conf.tv
``` in a script that opens a second X server using twinview across my primary monitor and my TV (otherwise it uses both monitors)

However, recently I updated my system and now it opens across both of my monitors, just like my default config. It seems that *X* is ignoring the *-config* argument. I confirmed this by running *nvidia-bug-report.sh* and it listed the config file as /etc/X11/xorg.conf instead of the /etc/X11/xorg.conf.tv as defined.

man x doesn't pull anything up. Anyone know what's wrong? I've been using this without a hitch for months...

Using xserver-xorg 7.0.0.0-0ubuntu40 and nvidia-glx 1.0.8756, although I don't think it's an nvidia issue.

---

