---
title: "X seemingly randomly crashing..."
date: 2012-06-05
forum: General Help
---

### Post by ragtag on 2012-06-05
I have Ubuntu 12.04 64 bit on several machines, and on one of them, X seems to randomly crash and log me out. The following error is in syslog.


```
Jun  5 16:35:06 lin00 avahi-daemon[1025]: Invalid response packet from host 10.0.0.251.
Jun  5 16:36:11  avahi-daemon[1025]: last message repeated 3 times
Jun  5 16:37:15  avahi-daemon[1025]: last message repeated 4 times
Jun  5 16:38:10 lin00 kernel: [ 4612.045813] do_general_protection: 27 callbacks suppressed
Jun  5 16:38:10 lin00 kernel: [ 4612.045818] Xorg[5538] general protection ip:7f744d9f06a9 sp:7fff62b26c30 error:0 in nvidia_drv.so[7f744d98f000+6e0000]
Jun  5 16:38:11 lin00 gnome-session[5706]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.#012
Jun  5 16:38:11 lin00 acpid: client 5538[0:0] has disconnected
Jun  5 16:38:11 lin00 acpid: client 5538[0:0] has disconnected

```

The machine is a dual quad core box with Nvidia Quadro 3800FX graphics card, and the default proprietary driver installed.

I've also seen similar behaviour with a laptop with integrated Intel graphics card.

Any idea what is going on?

---

