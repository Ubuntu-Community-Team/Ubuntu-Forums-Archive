---
title: "&quot;frequency scaling unsupported&quot; at startup, other threads don't help"
date: 2009-08-28
forum: General Help
---

### Post by jjjjeremy on 2009-08-28
I know that this *has* to be an easy fix. I was trying to get some extra battery life out of my laptop, now I just get "Frequency scaling unsupported" at startup, and I want it to go away. I don't care about  CPU frequency scaling anymore.

Compaq Presario C500
Motherboard 30C6
Currently running w/o battery, haven't tried with battery, but I doubt that will make a difference

Was working off of this [http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)


I added CPU Frequency Scaling Monitor to panel.
Ran sudo dpkg-reconfigure gnome-applets
Selected Yes for SUID
Exited
Left click on CPU Frequency Scaling Monitor
Nothing (well, a tiny bar appeared beneath)
Restart
Search around BIOS, find nothing
"frequency scaling unsupported" at startup
Restart
Search around BIOS, find nothing, again
Restart
"frequency scaling unsupported"
Ran sudo dpkg-reconfigure gnome-applets
Selected No for SUID
Exited
Restart
"frequency scaling unsupported"
Removed CPU Frequency Scaling Monitor from panel
Restart
"frequency scaling unsupported"
Restart
"frequency scaling unsupported"
Restart
"frequency scaling unsupported"
Bash head against wall.

---

### Post by jjjjeremy on 2009-08-28
Still happening, considering re-installing just to get rid of it

---

### Post by Youresorock on 2009-08-29
I'm gonna chime in on this one.  My main linux machine at home is a Celeron 430, 1.8Ghz.  I know it supports frequency scaling because it works in FreeBSD.  Maybe linux is behind?  I don't know.


I did some research, and the normal modprobe method is gone for this.  Everything has been built into the kernel since around April it appears.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355232](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355232)

I realize my CPU is not the best, but it's more than fast enough for everything other than gaming.  It sucks that it has to waste watts while idle, when in FreeBSD it scales down to 451Mhz.

Anyone had any luck?  Know the secret?  The FreeBSD package to do this is powerd if anyone is curious.

---

### Post by BuckleyInDaHouse on 2009-08-29
Do you have an AMD cpu?

---

### Post by jerome1232 on 2009-08-29
Make sure it's enabled in your bios, amd calls it cool n quiet I don't know what intel calls it.

---

### Post by jjjjeremy on 2009-08-29
I broke down and re-installed.

---

