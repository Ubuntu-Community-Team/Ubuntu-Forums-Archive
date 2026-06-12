---
title: "How do I modify the startup script?"
date: 2004-10-21
forum: General Help
---

### Post by Perfect Storm on 2004-10-21
As the the headline says, I want to modify the startup script.

I'm trying to get Mplayer to run perfectly and it suggest I add '**echo 1024 &gt; /proc/sys/dev/rtc/max-user-freq**' to the script due to the Perssion denied error: *Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied*


.:=The A.I. Dude=:.

---

### Post by Perfect Storm on 2004-10-21
*bump*

---

### Post by adbak on 2004-10-21
I don't know *how* you do it, but you somehow have to create an init script in /etc/init.d then link it to /etc/rc.&lt;x&gt;/dir.  That's all I know.  Perhaps you could use [http://www.google.com/linux](http://www.google.com/linux) to search for a "how to".

---

### Post by JProgrammer on 2004-10-21
you can just add it to your /etc/inittab file and it will run on every boot

---

