---
title: "Suddenly, the network applet became an indicator applet"
date: 2011-01-18
forum: General Help
---

### Post by Quadunit404 on 2011-01-18
Yeah. For whatever reason my Network Applet became an Indicator Applet today and I don't know why. I am pretty sure I am still on Ubuntu 10.10 as when I look in the System Monitor it says my Kernel is Linux 2.6.35, the OS is Ubuntu and the release is 10.10. The SM doesn't lie, now does it?

I guess it's fine, but the VPN menu has vanished (the "VPN Connections" label is still there but the menu is not) and I can't bring up the About dialog, nor the Connection Information and the Edit Connections dialogs. Along with that, I cannot do basically anything with it beyond open up the menu.

But hey, I'm still connected to the Internet, so as long as it has that working I'm (mostly) fine, right?

---

### Post by Quadunit404 on 2011-01-18
Okay, so apparently my PC went through a time machine and upgraded itself to Ubuntu 11.04 - which isn't true. In the About Ubuntu dialog it says that I'm using Ubuntu 11.04, when I'm not actually using it. I've heard about a glitch like this before...

---

### Post by efflandt on 2011-01-18
Not quite sure what you mean by network applet vs. indicator applet.  But I have seen About Ubuntu show Natty 11.04 on a system that was just upgraded from 10.04 to 10.10.  But you are not likely really using Natty unless this command shows this:

efflandt@natty-ssd:~$ **cat /etc/*release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"

---

### Post by Quadunit404 on 2011-01-18
What I mean is that the Network Manager moved itself from the Notification Area to the Indicator Applets.

And I know I definitely did not accidentally upgrade because in the Session Manager on GDM I don't see "Ubuntu Classic Desktop" and I *never* install development releases of something on physical hardware, just virtual hardware.

---

### Post by Quadunit404 on 2011-01-18
```
tom@tom-laptop-linux:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

Yep, still on Maverick. The OS is now out of the way.

---

### Post by Quadunit404 on 2011-01-19
Sorry that I've been replying to this thread so much (maybe) but I just found the reason why: the Elementary Team ported the Network Manager to the Indicator Applets so that it'll display in their WingPanel. Granted, it's a glitchy port, but hey, if it works and it displays in WingPanel, it's fine.

---

