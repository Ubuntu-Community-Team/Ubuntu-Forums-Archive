---
title: "Laptop suspends when pluging off the charger"
date: 2011-08-28
forum: General Help
---

### Post by micael3000 on 2011-08-28
Hello,

When I have low battery and plug the charger, after some time (lets say 1 hour), if I pull of the charger (and the battery is now almost full charged) ubuntu just suspend the computer.
I had this issue before formatting but I do not remember how did I fix it.

Could anyone help me? ;)

---

### Post by magic8ball on 2011-08-28
I did some quick searching and it appears that Ubuntu is misinterpreting the AC disconnect as a laptop lid closed event.  It looks like some people go into power management and, for when "On Battery Power", they change the "when laptop lid is closed" setting to "blank screen" to speed up the recovery (i.e. getting out of blank screen faster than getting out of suspend).

There also appear to be some possible workarounds to disable the feature.  Maybe on of these links will help you remember how you fixed it before (or at least point you in the right direction):

[http://ubuntuforums.org/showthread.php?t=1614861](http://ubuntuforums.org/showthread.php?t=1614861)

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/499170](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/499170)

[https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/451433](https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/451433)

Good Luck.

---

### Post by micael3000 on 2011-08-29
Hello,

Thanks for your answer!
But none of these are the real solution heh... My laptop close lid default action was blank screen long time before this issues, therefore, this is not the correct solution and not the correct bug... :)

I remember setting something up about the percentage of the battery that ubuntu uses to suspend when battery is low... Or something about 'refreshing' the battery charge level before checking if it is low in order to suspend.

I am sorry because I really do not remember how I have fixed it before (i really did found something over the Internet that really worked for me).

Thank you!

---

### Post by micael3000 on 2011-09-08
Bump, it is still happening. :/

---

