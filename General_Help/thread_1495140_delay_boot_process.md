---
title: "delay boot process"
date: 2010-05-27
forum: General Help
---

### Post by Bufke on 2010-05-27
Well this may be an odd request for help but I'm trying to make the boot process slower. It seems likewise open has issues connecting right away. So when a user immediately tries to log in it doesn't let them and says authentication error making the user think the computer is broke.  If I let the computer sit still for about 2 minutes it works fine.

I'm thinking a work around would be to perhaps delay gdm but I'm not sure how this is done.  Putting sleep 60 in /etc/init.d/gdm doesn't work. How can I delay startup? Naturally I need networking and likewise open to be running while gdm waits a bit.

---

### Post by dcstar on 2010-05-27
> **Bufke said:**
> Well this may be an odd request for help but I'm trying to make the boot process slower. It seems likewise open has issues connecting right away. So when a user immediately tries to log in it doesn't let them and says authentication error making the user think the computer is broke.  If I let the computer sit still for about 2 minutes it works fine.

I'm thinking a work around would be to perhaps delay gdm but I'm not sure how this is done.  Putting sleep 60 in /etc/init.d/gdm doesn't work. How can I delay startup? Naturally I need networking and likewise open to be running while gdm waits a bit.

The Ubuntu boot process has been deliberately quickened through use of Upstart which starts a lot of things in "parallel" rather than waiting for one thing to finish before loading another, some older packages do not take this into account and start up before other dependencies have loaded.

Change the order that the particular package loads in the /etc/rcN.d folders or put it in rc.local.

---

### Post by de Silentio on 2010-07-28
Bufke, I am having the same problem.  Did you figure out a resolution?
 
Thanks.

---

### Post by kizmou on 2010-07-30
bump

---

### Post by Bufke on 2010-09-14
Hey sorry I haven't worked on this in some time.

It is possible to delay the boot process

edit /etc/gdm/Init/Default

add as the first line ping -W 30 -c 1 [www.google.com](www.google.com)

What it does is tries to ping google before starting gdm. It stops as soon as it pings but has a timeout of 30. 

An quick test shows it works to help make active directory useful but I'll do more testing later.

I started a thread about this also at [http://community.centrify.com/t5/DirectControl-Express/Wireless-can-t-log-in-right-away/td-p/171](http://community.centrify.com/t5/DirectControl-Express/Wireless-can-t-log-in-right-away/td-p/171)

---

