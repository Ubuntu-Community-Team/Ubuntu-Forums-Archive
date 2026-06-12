---
title: "Low FPS unless root"
date: 2010-12-23
forum: General Help
---

### Post by djeikyb on 2010-12-23
**Problem:**
Normal users aren't using the best graphics driver. I first noticed this playing Osmos from the HumbleBundle2, but I can observe it while running glxgears too. Maximised on a 1280x1024, glxgears averages a choppy 60 frames in 5 seconds, vs a smooth 300 frames every 5 seconds for root.

Here's some glxinfo:```
jake@daedalus:~$ glxinfo | grep "renderer string"
OpenGL renderer string: Software Rasterizer
jake@daedalus:~$ sudo glxinfo | grep "renderer string"
[sudo] password for jake: 
OpenGL renderer string: Mesa DRI R300 (RV380 5B60) 20090101 x86/MMX+/3DNow!+/SSE2 TCL DRI2
```
I have the same problem even after rebooting (powering down, cycling surge protector). I followed the directions at the [Ubuntu wiki for getting rid of fglrx](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver), but no dice. What else can I do?

**Hardware:**
Radeon x300
AMD Athlon 1.8 GHz
1.5 GB ram

---

### Post by djeikyb on 2011-01-24
I found my solution at askubuntu.com: [http://askubuntu.com/questions/22993/why-do-i-have-low-fps-unless-root](http://askubuntu.com/questions/22993/why-do-i-have-low-fps-unless-root)

It was simple as adding my normal user account to the video group.
```
adduser jake video
```

---

