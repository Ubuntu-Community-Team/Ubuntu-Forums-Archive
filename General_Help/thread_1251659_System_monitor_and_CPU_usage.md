---
title: "System monitor and CPU usage"
date: 2009-08-27
forum: General Help
---

### Post by abrari on 2009-08-27
Sometimes I got a program stopped working with high CPU usage. It's windows has closed, but the CPU usage is still high. I opened system monitor to see which program causes that high CPU usage. But I found nothing. But the entire system still slowed down.

The system monitor **applet** shows high CPU activity, but on (real) system monitor, the highest CPU usage is the gnome-system-monitor itself (and compiz sometimes). I can't find which program is eating my CPU.

So, if that happened, all I can do is logging out and in again. On some case, I have to restart the system.

My system has dual-core processor (I can see 2 processors on system monitor). Any relation with that?

---

### Post by hwttdz on 2009-08-28
Try "top -b -n 1", you can post it here if you like, look for processes which have high cpu usage or memory usage.

---

### Post by P4man on 2009-08-28
In system monitor, processes, click "view", then select "all processes" rather than just your own. Of course top works fine too :)

---

### Post by abrari on 2009-08-28
> **P4man said:**
> In system monitor, processes, click "view", then select "all processes" rather than just your own.

Oh, I've never see that options :P
On "all processes" I can see Xorg.
I guess it is Xorg that behaves badly sometimes.

Thanks for all...

---

