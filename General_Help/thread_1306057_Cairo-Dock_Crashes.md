---
title: "Cairo-Dock Crashes"
date: 2009-10-30
forum: General Help
---

### Post by cel13 on 2009-10-30
I changed theme on cairo dock and dock disappeared and all I get is this configuration window, and if I click quit the window opens again. I tried reinstalling but it didn't help.

Could anyone help me please ?

---

### Post by razy60 on 2009-10-30
Hi, Is it in applications-tools.
If it does not work from there you need to uninstall via Synaptic or add remove then restart then either install via synaptic or terminal.
There are a few help threads on how to do it in terminal.

Raz

---

### Post by cel13 on 2009-10-30
I removed it using terminal like this sudo apt-get remove cairo-dock and then sudo apt-get autoremove. And I installed it like this: sudo apt-get install cairo-dock.

---

### Post by razy60 on 2009-10-30
I had to completely remove all traces of it from synaptic before i could re install it, i used the download from the site,
I dont have it any more so i am having to dig through the memory which is proving to be hard:-k.


Raz

I think i had to disable compiz install then restart compiz before it would run.

---

### Post by fabounet on 2009-10-30
which version do you use ?
the latest stable one is 2.1.1-2

which theme did you choose ?

---

### Post by cel13 on 2009-10-30
I have latest stable version and I chose Mac OS X theme.

---

### Post by faical117 on 2009-10-30
TRY DELETING ALL TRACES WITH THIS COMMAND:
sudo apt-get purge cairo-dock cairo-dock-core cairo-dock-data cairo-dock-plug-ins cairo-dock-plug-ins-data cairo-dock-plug-ins-integration

---

### Post by cel13 on 2009-10-30
I did that, but it didn't help..
I installed it again and when I open it config window opens and it's saying Maintenance mode and still I can't close it.


I don't what happened but now suddenly it is working, thanks all.

---

