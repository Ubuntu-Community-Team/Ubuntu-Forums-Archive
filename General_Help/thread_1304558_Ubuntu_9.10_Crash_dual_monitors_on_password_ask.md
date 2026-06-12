---
title: "Ubuntu 9.10 Crash dual monitors on password ask"
date: 2009-10-29
forum: General Help
---

### Post by Isaacgallegos on 2009-10-29
When ever I have to install something using dual monitors, I get a window asking me for a password. When it pops up my system lags very bad then crashes. When I have only one monitor running there is no problem with this window. 

Do I just wait this problem out until there's a fix? 

Nvidia 8800GTS

---

### Post by P4man on 2009-10-29
I have the same problem and reported a bug The problem for me goes away after installing the nVidia restricted drivers. Bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/447171](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/447171)

Perhaps you can confirm it

---

### Post by Isaacgallegos on 2009-10-29
What are restricted drivers? Are those the ones of the website?

---

### Post by P4man on 2009-10-29
Restricted means they are not opensource, so simply the nvidia drivers the  "hardware drivers" applet in system > administration will propose for your card, or the ones from nvidia site. (But unless you have a specific reason not to, just use the ones recommended by the "hardware drivers" application).

---

