---
title: "Amarok crashing fix!"
date: 2006-03-18
forum: General Help
---

### Post by Luggy on 2006-03-18
I was running Amarok on Gnome for a long time and then all of a sudden it decieded to crash on me: it wouldn't start and was trying to launch kMail to contact the devs to notify them of an error.

I tried to remove and completely remove amarok from my system using synaptic but to no avail. Eariler today I was checking out the Amarok bugzilla and fourms and got posted to a similar error where the fix was to remove an xml file in ~/.kde/share/apps/amarok/. I figured I would give it a go but I had my doubts considering that I have completely removed it from my system. 

Lo and behold the directory was still there. I then removed the directory
```
rm -r ~/.kde/share/apps/amarok/
```
and installed amarok using synaptic and now it works.

---

### Post by ComplexNumber on 2006-03-18
this can apply to many packages. when a package is uninstalled, the configuration files in one's home directory always remain....so these often need deleting too.
this is quite a useful fix for many people because many want to run amorak on gnome.

---

