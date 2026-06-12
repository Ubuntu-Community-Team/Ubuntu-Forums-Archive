---
title: "Skype causes X-Server to crash"
date: 2010-10-22
forum: General Help
---

### Post by Ron Jones on 2010-10-22
I just installed skype 2.1.0.81-1ubuntu5 on my 10.10 desktop.

Then I chose Applications > Internet > Skype and accepted the terms of use. Whereupon the Xserver immediately crashed, the screen went dark, and after a few seconds, I was presented with the login screen.

I restarted the computer, attempted to open skype again; and again the Xserver crashed.

I'm using a GeForce GT 240 video card by Gigabyte, as well as the Nvidia-supplied driver (as opposed to the stock Ubuntu-supplied driver) and the "Nvidia X Server Settings" application.

Can someone point me in the direction of a set of troubleshooting steps?

I'm new to Ubuntu, but I've been a casual Linux user for long enough to be comfortable with the command line, and config files (though I still have to google up all but the most basic commands).

Thanks,
Ron

---

### Post by 666f6f on 2010-10-22
[bug #657966]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/657966") may be relevant..

---

### Post by Ron Jones on 2010-10-22
Well, it certainly sounds right. But I'm only running one monitor, and cannot find a reference to Xinerama (in order to disable it) anywhere in my Nvidia configuration tool.

---

### Post by 666f6f on 2010-10-22
It's not necessarily the Xinerama/Dual monitor setup that causes the crash.

You could participate to the bug discussion and report your experience there.

I'm not claiming that the linked bug is the cause of your problem, I'm only suggesting, maybe I'm wrong.

---

