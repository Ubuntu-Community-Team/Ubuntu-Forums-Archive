---
title: "Ubuntu and External Monitor Problem"
date: 2010-08-20
forum: General Help
---

### Post by bpejman on 2010-08-20
Hi,

I have a Sony Vaio VGN-S460 laptop running Ubuntu 10.04 LTS with the latest updates and kernel  running on 32bit arch.  For some reason, my Fn keys don't work and I want to go from a 13.3" screen to a 23" external monitor.  The monitor I'm trying to connect to is a Samsung so it's not a crazy unknown manufacturer (if that even matters).

Does anyone know how I can do this without modifying my xorg.conf file and running a command each and every time?  If I have to modify xorg.conf, I'm okay with it but I don't want to do it every single time.

There has be an easier way.  If external monitor is not supported in 10.04, it's completely fine but I just want to know.

Thanks!
Bobby

---

### Post by Morrad on 2010-08-20
Have you tried using the tool in the system menu?

System -> Preferences -> Monitors

---

### Post by bpejman on 2010-08-20
Thanks for your reply.  I have tried the Monitors option under preferences but the problem is it doesn't detect my external display.

So, here's what I have done so far as a work around.  I have created two xorg.conf files: one called **xorg.conf.sony** and the other called **xorg.conf.samsung**.

If I load the Sony conf file, only my laptop display works.  If I load the Samsung conf file, only my external monitor works and my laptop LCD remains off.  For now this is great.  By the way, when I say "load" I mean copy and overwrite the desired conf file over the original xorg.conf.

I just got an idea.  Is there any X11/display command I can run and feed a custom xorg.conf.* file to it?  I want to simulate restarting X11 just like when you log off your system.  Then, I can write up a script and off I go.

Any help would be really appreciated!!

---

### Post by jbev on 2010-08-20
Sounds like you don't have a good enough graphics card...If you are just using an onboard graphics card it may not be able to handle the display

---

