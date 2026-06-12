---
title: "Hard drive add?"
date: 2011-02-10
forum: General Help
---

### Post by reborn7778 on 2011-02-10
hello, everyone. 

today, i am installed everything seem fine, so but one problem, i felt so idiotic, seriously, because i need to add an available in hard drive, yet, i just uploaded a picture, and you see a red circle, where an available, so where i can find to add like 50 gb available? pleasee thanks!

---

### Post by JohnnyC35 on 2011-02-10
ext4, and I think ext3, reserve space automatically. Here's a couple links you can follow to adjust the amount saved. Or you could use a different filesystem.

[http://tombuntu.com/index.php/2009/03/11/free-disk-space-by-reducing-reserved-blocks/](http://tombuntu.com/index.php/2009/03/11/free-disk-space-by-reducing-reserved-blocks/)

[http://www.winxperts.net/forums/topic/1280-how-to-shrink-reserved-space-ext4/](http://www.winxperts.net/forums/topic/1280-how-to-shrink-reserved-space-ext4/)

hope that helps :)

---

### Post by P4man on 2011-02-10
He is using WUBI! Please ignore the above, it wont work for you.
You can try this:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

Or better, if you like ubuntu, do a regular install from ubuntu cd (or usb) and dont use wubi.

---

### Post by Mark Phelps on 2011-02-10
Just so other know ... the "/host" is what indicates this is a Wubi install.

Since folks often use Wubi, and don't remember they did, BEFORE offering any advice regarding partitioning, ALWAYS try to determine whether or not they have a Wubi install.  Traditional partition solutions will NOT work with a Wubi install.

---

### Post by reborn7778 on 2011-02-10
> **P4man said:**
> He is using WUBI! Please ignore the above, it wont work for you.
You can try this:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

Or better, if you like ubuntu, do a regular install from ubuntu cd (or usb) and dont use wubi.

well, a couple of month ago i have a tried a ubuntu to installed on my laptop, it is all of black. i was confused, and lazy to fix, so i found Wubi is seem pretty good, so. it is worked for me.

---

### Post by P4man on 2011-02-10
All of black? if you mean you ended up with a black screen, see the link in my signature for a likely solution.

Anyway, its up to you, but wubi really isnt a long term solution, and sooner or later it will break (especially doing upgrades). But if you want, the above link might help you increase the amount of space you have for your wubi install.

---

### Post by reborn7778 on 2011-02-10
> **P4man said:**
> All of black? if you mean you ended up with a black screen, see the link in my signature for a likely solution.

Anyway, its up to you, but wubi really isnt a long term solution, and sooner or later it will break (especially doing upgrades). But if you want, the above link might help you increase the amount of space you have for your wubi install.

You got me, and i am been thinking, and i just uninstall them, and i will download to CD.  is it will be work for my laptop? and include boot dual?

---

### Post by P4man on 2011-02-10
Find out if it works, I dont make any promises. 

But you can just boot the live cd using the nomodeset "trick" and try the OS without even installing. If it works fine, reboot in to your wubi install and backup whatever needs backing up. Then reboot in to windows, to uninstall wubi (simply like you uninstall windows software), then boot the ubuntu cd again, and install it. And yes, it will set up dual boot if you ask it to. It will even resize your existing windows partitions and create the ones it needs. Its rather idiot proof.

---

### Post by reborn7778 on 2011-02-10
> **P4man said:**
> Find out if it works, I dont make any promises. 

But you can just boot the live cd using the nomodeset "trick" and try the OS without even installing. If it works fine, reboot in to your wubi install and backup whatever needs backing up. Then reboot in to windows, to uninstall wubi (simply like you uninstall windows software), then boot the ubuntu cd again, and install it. And yes, it will set up dual boot if you ask it to. It will even resize your existing windows partitions and create the ones it needs. Its rather idiot proof.

ok thanks, i will let you know when find the result.

---

