---
title: "starting gui"
date: 2006-02-10
forum: General Help
---

### Post by Disastorm on 2006-02-10
I am trying out ubuntu using the Live Cd on my laptop , I have an ati radeon xpress 200m and I read i should set the driver thingy to "vesa" but when i do that it still doesnt work
it says 

(EE) VESA(0): No Matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by dcstar on 2006-02-10
[QUOTE=Disastorm]I am trying out ubuntu using the Live Cd on my laptop , I have an ati radeon xpress 200m and I read i should set the driver thingy to "vesa" but when i do that it still doesnt work
it says 

(EE) VESA(0): No Matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/QUOTE]
Possibly the Live CD will always use the default video drivers that don't work with your hardware, so you may only get Ubuntu working by doing a full install and then following the instructions at:

[http://ubuntuforums.org/showthread.php?t=127344&highlight=ati+radeon+xpress](http://ubuntuforums.org/showthread.php?t=127344&highlight=ati+radeon+xpress)

---

### Post by Disastorm on 2006-02-10
I dont think this is the case because when I change it to "ati" i get a different error message than "vesa"

---

### Post by Disastorm on 2006-02-11
Is it possible that even tho i get different error messages, some part involves me having to reboot (which I think wont do anything with a Live CD), so I'd have to install it normally, or do you generally not have to reboot after switching from ati to vesa?

---

### Post by mirshafie on 2006-02-11
Disastorm:

You generally never have to reboot Linux, ever. Sometimes you need to restart X (graphics), which you can do by Ctrl+Alt+Backspace. That will either bring you to a terminal or to gdm (the Gnome login screen). If it brings you to a terminal, login and type 'startx' or 'gdm' to start Gnome again.

I'm not sure this will help, but you can try it if you want.

---

