---
title: "Can't enable visual effects after update"
date: 2011-10-19
forum: General Help
---

### Post by ccdwiu on 2011-10-19
Looking for some help!
I updated via update manager today. Since I restarted, my graphics have taken a turn for the worse. Normally, I have Extra Graphics enabled (going to System -> Preferences -> Appearance). If I try to enable Extra Graphics or even normal graphics, it searches for drivers and does not find any. 

Ubuntu 10.04

Here is a list of previously installed packages from today (10/19)

ommit Log for Wed Oct 19 08:19:05 2011

```

Upgraded the following packages:
byobu (2.68-0ubuntu1.1) to 2.68-0ubuntu1.2
libapache2-mod-php5 (5.3.2-1ubuntu4.9) to 5.3.2-1ubuntu4.10
libdevkit-power-gobject1 (1:0.9.1-1) to 1:0.9.1-1ubuntu1
libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.9) to 1.8.1+dfsg-2ubuntu0.10
libk5crypto3 (1.8.1+dfsg-2ubuntu0.9) to 1.8.1+dfsg-2ubuntu0.10
libkrb5-3 (1.8.1+dfsg-2ubuntu0.9) to 1.8.1+dfsg-2ubuntu0.10
libkrb5support0 (1.8.1+dfsg-2ubuntu0.9) to 1.8.1+dfsg-2ubuntu0.10
libupower-glib1 (0.9.1-1) to 0.9.1-1ubuntu1
php5-common (5.3.2-1ubuntu4.9) to 5.3.2-1ubuntu4.10
php5-mysql (5.3.2-1ubuntu4.9) to 5.3.2-1ubuntu4.10
upower (0.9.1-1) to 0.9.1-1ubuntu1
xserver-common (2:1.7.6-2ubuntu7.6) to 2:1.7.6-2ubuntu7.8
xserver-xorg-core (2:1.7.6-2ubuntu7.6) to 2:1.7.6-2ubuntu7.8
```

And here is an output for lspci:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```


Does anybody know how I can fix this?

---

### Post by r1ft on 2011-10-19
I came here to post this exact thing. I am running 64-bit Lucid on a Penryn Core2Duo (Intel 4 series graphics).

I thought the issue was with my Compiz (v0.8.6) when my window decoration settings (and keybindings) didn't work.

EDIT: Emergency bugfix is coming: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905)

---

### Post by ccdwiu on 2011-10-19
Awesome, thanks so much for posting this!

---

