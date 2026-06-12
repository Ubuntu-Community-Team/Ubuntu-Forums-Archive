---
title: "Issues with new install of 9.10"
date: 2009-11-27
forum: General Help
---

### Post by gspat on 2009-11-27
Hi, I'm generally happy with 9.10 as it is, but I've had some issues getting it going and some still outstanding issues I'd like to resolve.

1). (sort of resolved) Initial boot after install brought me to a text login. 

sort of resolved this by following a posting I found to install the NVIDA 190 driver using recovery mode. GUI now works, but had to install nvidia-glx package.

Should I be downgrading to NVIDIA 185 driver to make nvidia-glx-185 happy? Will this cause me instability later on?

2). Programs that should autostart at system boot up either do not start or at least do not show up in the notifications area.

lots of searching and I don't find alot of recent info about this one, as an example, I have gnome-do set to load at startup... but it doesn't... I have to either run it from the menus or from the terminal. This is not the behaviour I desire. some programs seem to be running but put nothing in the notification area, others such as compiz have to be started by running the compiz-fusion-icon, waiting for it to then show up in the notification area and and then click on reload window manager. This will not work in the terminal at all it just gives:

compiz --replace
aborting and using fallback: /usr/bin/metacity

3). Wine installs, but nothing runs besides notepad and regedit. and some weird font thing is happening where it can't download a font is now taking over sudo apt-get upgrade.

What is the deal with andale32 anyways? anything I try to run in wine now either sits dormant on a splash screen, or simply errors out. The appdb at winhq says that what I'm trying to run is platinum, so this shouldn't be an issue.

---

### Post by checoimg on 2010-01-20
I always test Wine with the free client software from [www.playchess.com](www.playchess.com).

---

