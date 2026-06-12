---
title: "Symlinking a /usr folder from another partition to /opt/&lt;dir&gt;"
date: 2009-11-12
forum: General Help
---

### Post by nerdopolis on 2009-11-12
Hi I am trying to find an easy way to temporarily 'add' some programs (some graphical programs that utilize libraries) into an Ubuntu system, by symlinking a /usr folder from another partition (/media/mount/usr) to /opt/temp/. The symlinking part is easy, but how do I tell the system that the programs are there? I know PATH is for binaries, and SHLIB_PATH and LD_LIBRARY_PATH is for some libraries, (but I'm not quite sure if the last work...), but are there other variables I should consider that I don't know about? 

Thanks.


Edit: I am not symlinking them, I am now using mount --bind.

---

### Post by nerdopolis on 2009-11-16
OK. I have KDE Neon installed on one of my Ubuntu's (and it places itself in /opt/kde-neon, and it creates these variables. 
LD_LIBRARY_PATH
SHLIB_PATH
QT_PLUGIN_PATH
XCURSOR_PATH
XDG_DATA_PATH
PATH

Are there any more that I should be concerned about setting? I'm sure I'm missing some others.

---

