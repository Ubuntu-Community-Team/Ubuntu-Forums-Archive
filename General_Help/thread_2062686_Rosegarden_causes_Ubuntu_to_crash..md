---
title: "Rosegarden causes Ubuntu to crash."
date: 2012-09-25
forum: General Help
---

### Post by davemar on 2012-09-25
I've just installed rosegarden and when it starts up OK, but when I select the open file icon it brings up the file selector window for a split second then crashes the whole OS, causing it to reboot.

I've never know any program to actually crash Ubuntu!

I can rosegarden for the command line and redirected stderr to a file to log any errors. The final message was:
```
rosegarden: Fatal IO error: client killed
```
Nothing before it indicating any problems.

I'm running 12.04LTS 64-bit. Rosegarden is the latest install from synaptic.

Has anyone else experienced this?

---

### Post by davemar on 2012-09-26
I've also found kate crashes the desktop as well, so there's a common link there. I installed the latest NVIDIA drivers in case that was the problem, but that hasn't cleared up the problem.

BTW, I'm using gnome as I can't get along with Unity.

---

### Post by HiImTye on 2012-09-26
does Rosegarden use OpenGL? it might be an issue with nVidia drivers. try the open source ones and see if it fixes it.

you might want to take a look at /var/log/kern.log and var/log/syslog

---

### Post by davemar on 2012-09-26
I don't think it uses OpenGL, and torcs (OpenGL game) runs fine. Nothing in those two log files indicating anything going wrong either.

---

