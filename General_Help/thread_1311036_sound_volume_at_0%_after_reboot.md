---
title: "sound volume at 0% after reboot"
date: 2009-11-02
forum: General Help
---

### Post by Irishpolyglot on 2009-11-02
I'm glad to report that everything went smoothly after upgrading to Karmic! :) (this was not the case in previous upgrades for me). I only have very minor errors, most of which I've eliminated. I believe this is the last one.
I always leave the sound at around 80% level, but after a reboot, it always starts at 0% (not muted, the scroll bar is at the bottom). I can't hear the log-in music etc. because of this. How can I force it to remember the sound level?
Thanks :)

---

### Post by khelben1979 on 2009-11-02
Have you tried setting the volume with [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")? It might be able to set the sound level permanent.

```
sudo apt-get install alsamixergui
``` if it's not already installed.

---

### Post by Irishpolyglot on 2009-11-02
Thanks, I tried alsamixer (already installed), and rebooted and the sound was still off until I adjusted it. Is there something specific you are supposed to do in Alsamixer? I just twiddled the volume to the top and pressed Esc to save. I don't think that will help me much.
Any other suggestions? :)

---

### Post by khelben1979 on 2009-11-02
I remember that I have had this problem which you have mentioned myself, although I'm using Debian.

A possible solution could be that you find a good sound volume application which saves your sound settings and then you exit your X server session and reboot the system to see if it's been fixed. 

I don't know what application you should use, but there's a couple to experiment with and I suggest you do this. Having super user priviliges before you open the sound settings application might help.

---

### Post by Irishpolyglot on 2009-11-05
I don't think an application is the issue here. Some setting has gone wrong since I upgraded to 9.10.
I'd appreciate anyone's suggestions..

---

### Post by peculiar penguin on 2009-11-05
Does something like

```
amixer set Master unmute 80%
```work for you after booting? I guess one could put that in rc.local, or run it as a script via Startup Applications.

---

### Post by peculiar penguin on 2009-11-05
Double post

---

