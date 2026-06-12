---
title: "Live CD not booting"
date: 2009-12-09
forum: General Help
---

### Post by anoovis on 2009-12-09
I am not able to boot the Karmic live CD or start  the installer. When booting live cd, it ends with a "out of range" message from the monitor. But I can access the terminal. This is the error i get when tries to stop the gdm

Rather than invoking init scripts through /etc/init.d, use the service(8)utility, e.g. service gdm stop
Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop gdm

Selecting safegraphics mode also failed. Jaunty was working fine. What caused the error ?

---

### Post by SteveNorman on 2009-12-09
what happens if you ```
startx
``` at the terminal?

BTW my first guess is its a bad cd since your last one worked.

---

### Post by anoovis on 2009-12-09
getting some error when running startx. gdm is already running.

---

### Post by SteveNorman on 2009-12-09
try cntrl-alt-f7

---

### Post by anoovis on 2009-12-09
when pressing ctrl+alt+f1 to f6 i'm able to run terminal. but could see the error message when f7

---

### Post by SteveNorman on 2009-12-09
try ```
stop gdm
```

then ```
startx
```

looks like there is a bug causing the upstart thing

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224)

---

### Post by anoovis on 2009-12-09
but i cant stop gdm when stopping gdm im getting an error 

"Rather than invoking init scripts through /etc/init.d, use the service(utility, e.g. service gdm stop
Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop( utility, e.g. stop gdm"

---

### Post by SteveNorman on 2009-12-09
Im stumped about that, like I said I think making a new live cd is in order, as the problem has to exist there since its not loaded to your HD. There may be a chance that post install you can fix it, but you want your live cd to work before you install from it.

I hate to do this to you but I have to get to bed, If you can get on IRC I would go to freenode#ubuntu

[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

good luck!

---

