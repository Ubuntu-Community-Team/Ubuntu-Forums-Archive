---
title: "shutdown impossible"
date: 2010-06-12
forum: General Help
---

### Post by DrScum on 2010-06-12
after upgrading to lucid very often a shutdown is impossible if I try to nothing happens. I have to open a terminal and enter "sudo halt". If you just enter "halt" you get "need to be root". This is annoying. Is there a way around this?

---

### Post by SoftBlue on 2010-06-12
I'm not enjoying having the same problem, but with a little different background. My Lucid Lynx install is fresh. I did not have the problem upon original installation. Post installation work has included upgrading to the video driver associated with the machine. This was handled by Ubuntu automatically and with permission. My video card is Nvidia GeForce 9100.
 
The reason I mention the video card driver as a suspect is because it seems that this may have been a problem within an earlier Ubuntu release. Positive resolution was not discovered.
 
The exact behavior of "shudown impossible" in my case is that selecting shutdown causes a logout only. In order to turn the machine off, it has to be turned off manually.
 
Additional information, the same computer did not have this problem with the previous version of Ubuntu.
 
Thanks for your help.

---

### Post by hansdown on 2010-06-12
There is a bug report filed for this.

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/574331](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/574331)

Hopefully, it will be addressed soon.

---

### Post by ubunterooster on 2010-06-12
temporary solution below

---

