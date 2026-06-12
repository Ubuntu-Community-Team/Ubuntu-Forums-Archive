---
title: "Need to stop an application (GNOME)"
date: 2011-04-13
forum: General Help
---

### Post by suenda on 2011-04-13
I dont know what I installed or what i  removed, but as I start GNOME, some application starts up automatically  and quickly runs many instances.. I dont know which application is this  exactly, but it's launches so quickly, it's already filled my panel and  i dont know which process is it, dont know how do i stop it. However when i  use KDE, this particular application does not starts up.. Anyway i can  stop this application as i start GNOME ?? Thanks in advance

---

### Post by deathadder on 2011-04-13
In gnome you can go to "System->Preferences->Startup Applications" to see what's there. Some (like PuleAudio) need to run, but if you're not sure what you can stop, post back with the list of applications and we'll see what we can do to help.

---

### Post by SecretCode on 2011-04-13
As well as the list of programs in System > Preferences > Startup Applications, on the 'Options' tab, there's a check box for 'Automatically remember running applications' - this means even if the app is not in the list, if it was running when you logged out, it will try to restart it.

If there's nothing obvious, you could try (in a terminal window) typing "top" or "htop" - processes consuming CPU will be at the top of the list. Of course, this rogue app might not use much CPU once opened.

Finally, you could type (in a terminal window)
```
xprop _NET_WM_PID
```
then click on one of the rogue windows. It will reply with a process id. Then entering
```
ps -P processid
```
will tell you what command opened the window.

---

### Post by suenda on 2011-04-13
Well, it was none of the programs listed under startups.. it turned out to be nautilus. So, what i did is.. i killed nautilus and then.. tried to start nautilus again, it didnt start. Thunar worked fine. Then, i removed nautilus using apt-get and installed it back again using apt-get . Started nautilus, worked fine like before.. And, i tried logging out and logging in to see if still the problem persists.. However, new problem... there was none of desktop environments listed in the start-up. I had KDE and GNOME, i could see none of them. I tried rebooting and tried recovery mode and eventually failed graphics mode.. The desktop environments have disappeared. I guess I messed up with something while removing and installing nautilus. Lucky that i had windows on dual boot, i cud make it to this forum.. Anything can be done to restore gnome and/or KDE?? thanks in advance.

---

### Post by suenda on 2011-04-13
Well, i tried to installing gnome again by using :

apt-get -f install ubuntu-desktop

It worked fine. I got my GNOME as well as KDE back to how it was.. Thanks everyone for help

---

