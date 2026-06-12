---
title: "Unrecognized monitor on Intel graphics chip"
date: 2010-03-18
forum: General Help
---

### Post by xphelanx on 2010-03-18
I'm running Ubuntu 9.10 64 bit and my Intel graphics controller (listed by lspci as 82G965) will not recognize my 17" CRT (Dell P780) for what it is, and therefore I am restricted to 640x480 or 800x600 resolutions. Does anybody have some insight or a workaround that will allow me to use the resolutions that I know this monitor is capable of? I know it will go up to 1600x1200 as I've been able to get it to work on previous versions. This seriously restricts my viewing area for web pages and other things, not to mention not being able to run fullscreen games very well.
Thank you in advance for any info you can provide!

---

### Post by patchwork on 2010-03-18
If you are running the i910 driver, try disabling Desktop Effects.   There is a known bug in the driver that prevents native resolution on some monitors if Desktop Effects are enabled.

Right-click on the desktop > Change Desktop Background > Visual Effects > None

---

### Post by xphelanx on 2010-03-18
> **patchwork said:**
> If you are running the i910 driver, try disabling Desktop Effects.   There is a known bug in the driver that prevents native resolution on some monitors if Desktop Effects are enabled.

Right-click on the desktop > Change Desktop Background > Visual Effects > None
Thanks, but it still doesn't change anything. Should this require a reboot to take effect?

---

### Post by xphelanx on 2010-03-22
Bump? Reboot didn't help after turning off desktop effects...

---

