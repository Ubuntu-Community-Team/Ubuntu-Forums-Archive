---
title: "Why isn't Ubuntu 10.04 available as an upgrade??"
date: 2010-05-07
forum: General Help
---

### Post by The Digger on 2010-05-07
Can anyone out there please explain to me why I can't just download Ubuntu 10.04 straight onto my computer as a simple upgrade from the version 9.04 that I'm currently running? I don't want to have to go to all the hassle of burning an ISO disc. Simple, direct upgrades straight from the internet,have been available from virtually all previous versions, so why on earth not this one??? Thanks!

---

### Post by aysiu on 2010-05-07
> **The Digger said:**
> Can anyone out there please explain to me why I can't just download Ubuntu 10.04 straight onto my computer as a simple upgrade from the version 9.04 that I'm currently running? I don't want to have to go to all the hassle of burning an ISO disc. Simple, direct upgrades straight from the internet,have been available from virtually all previous versions, so why on earth not this one??? Thanks!
It should be available.

More details here:
[http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20%28Recommended%29](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20%28Recommended%29)

Otherwise, it's a bug that needs to be filed.

---

### Post by _0R10N on 2010-05-07
Upgrading to another distro is not the same thing that upgrading installed packages. That's why are treated separately. Still, you can upgrade your distro without downloading and burning any iso at all. You can simply run
```
sudo aptitude dist-upgrade
```

---

### Post by finlost on 2010-05-07
I think you have to upgrade to 9.10 before you can upgrade to 10.04

---

### Post by aysiu on 2010-05-07
> **finlost said:**
> I think you have to upgrade to 9.10 before you can upgrade to 10.04
Yes, I also wouldn't recommend skipping releases in an upgrade unless you are going from LTS (8.04) to LTS (10.04).

---

### Post by TurboThiago on 2010-05-07
My version is 9.10; there is an option to upgrade to 10.04 version. My prof's version is 8.10 I think. He said he have to upgrade to 9.04, after to 9.10 and after to the newest version: 10.04. I think you have to upgrade one by one as he said he would do,but I don't know if there is a way to do it with just one command. 

bye

Thiago

---

### Post by aysiu on 2010-05-07
By the way, it is a lot faster to just install a fresh 10.04 and then reinstall all your applications than to upgrade from 9.04 to 9.10 and then upgrade from 9.10 to 10.04.

---

### Post by lashram on 2010-05-07
You can try this in the terminal type  sudo update-manager -d

This is how I upgraded my Ubuntu Karmic(9.10) to Lucid(10.04) and it worked for me without a hitch. :guitar:

---

