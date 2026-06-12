---
title: "Trouble install realvcn ubuntu 10.04"
date: 2010-08-22
forum: General Help
---

### Post by Grimuth on 2010-08-22
Hey ive been trying to install REALvnc the free version using the package installer and it looked like it installed fine but when i went to click on the icon nothing would open, when I clicked on the "terminal" drop down display on the package installer, it has this error during the installation

"/usr/local/bin/vnckeygen: 1: Syntax error: ")" unexpected""

ive tried to cat this file and its all a bunch of jibberish.

i think it has something to do with my ubuntu because Ive installed the same thing on another Ubuntu machine, same version, with no error and it works fine.

Is there a way I can repair anything I may have broken on this version of ubuntu to not let me install this program?

---

### Post by dino99 on 2010-08-22
when this kind of issue is coming, the easiest way is remove/purge the installed broken package(s) then reinstalled them with synaptic

you can check your sources.list (synaptic repo tab) to be sure you only use lucid genuine repo, then clean the cache: clean, autoclean autoremove

and finally update, install -f and dpkg --configure -a

---

