---
title: "Why Blocked?"
date: 2009-07-12
forum: General Help
---

### Post by solarwind on 2009-07-12
I am running Kubuntu 9.04 and have updated all packages. However, the update manager says that the following packages are "blocked":

[[IMG]http://img27.imageshack.us/img27/3941/snapshot1l.th.png[/IMG]](http://img27.imageshack.us/i/snapshot1l.png/)

Why are they blocked?

Note that I'm using the AMD64 Kubuntu.

---

### Post by hansdown on 2009-07-12
Hi solarwind.

There is a solution in this thread. 

[http://ubuntuforums.org/showthread.php?t=1191493](http://ubuntuforums.org/showthread.php?t=1191493)

Post number 6 is the one you want.

---

### Post by darolu on 2009-07-12
You can try (on your konsole/terminal):
```
sudo aptitude -f full-upgrade
```
or
```
sudo apt-get -f upgrade
```

---

### Post by solarwind on 2009-07-12
Thank you very much for both of your replies. I will try to force the upgrade, but I just hope it wont render my system inoperable.

---

### Post by solarwind on 2009-07-12
Ok, dist-upgrade will work, but I cancelled it. I don't want to force the upgrade. There is a reason those packages are blocked. Maybe it's because the upgrade will break some packages. I want to know why they are blocked. How can I find the reason?

---

### Post by hansdown on 2009-07-13
It's likely because there is a kernel upgrade in there.

My version is running 2.6.28.13 generic kernel.

I think the person in that thread upgraded without problem.

Good to be careful though.

---

### Post by Chronon on 2009-07-13
One of the staff, HymnToLife, provides an explanation for why in post #11:
[http://ubuntuforums.org/showpost.php?p=7499891&postcount=11](http://ubuntuforums.org/showpost.php?p=7499891&postcount=11)

---

### Post by hansdown on 2009-07-13
Thanks for the extra info Chronon. I should have mentioned your name

in that thread.

Thanks to yabbadabbadont for the thankyou .png

---

