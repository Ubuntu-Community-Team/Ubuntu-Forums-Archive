---
title: "General question about update..."
date: 2009-07-12
forum: General Help
---

### Post by punia1979 on 2009-07-12
Hi all, have a quick one about system upgrade... First of all I am happy user of Ubuntu 8.1 system works perfect for me and is very stable! I have install lots of software like XBMC,compiz effects, cairo dock etc... my question is what's will happen when I choose to upgrade to 9.04 by the update manager? Do I gona loose all my settings? Do I gona have to configure everything one more time? What is the main difference between 8.1 and 9.04? is it more stable?

regards to all Ubuntu users ):P

---

### Post by -=hazard=- on 2009-07-12
Upgrading to 9.04 from update manager you dont loose anything, apart of any library or any software that might be no compatible with the new version, but anyway all settings remain untouched.

---

### Post by Martin Witte on 2009-07-12
Main differences between 8.10 and 9.04 are listed [here]("http://www.ubuntu.com/getubuntu/releasenotes/904overview")

---

### Post by DeMus on 2009-07-12
> **-=hazard=- said:**
> Upgrading to 9.04 from update manager you dont loose anything, apart of any library or any software that might be no compatible with the new version, but anyway all settings remain untouched.

True, but upgrading is not as good as installing a new OS from the ground up, meaning wiping the drives clean and start all over. This means you will loose everything, including your installed software and setting, but in return you get a much more stable system, free from everything which might be left from 8.10.
Can't you make a list of what you have now, programs, settings, etc. Then install a fresh Jaunty and with the list install everything again like it was. It's more work, I admit it, but you will gonna love the result.

---

### Post by punia1979 on 2009-07-12
and where I can find more info about the differences between this two distributions? And finally do U think I should upgrade if current 8.1 version works perfect for me?

---

### Post by DeMus on 2009-07-12
> **punia1979 said:**
> and where I can find more info about the differences between this two distributions? And finally do U think I should upgrade if current 8.1 version works perfect for me?

It depends. When it's running fine now and you don't need newer versions of programs, or the newer kernel then you can also stick with 8.10 for now. I did change from Hardy to Jaunty because I am nosy. I skipped Intrepid cause I read a lot of bad things about it when it arrived, but I could not resist installing Jaunty. And I must honestly say: I love it.

Maybe you have seen this already, but in case you have not, take a look here:
[http://www.ubuntu.com/products/whatisubuntu/904features/]("http://www.ubuntu.com/products/whatisubuntu/904features/")

---

### Post by -=hazard=- on 2009-07-12
> **punia1979 said:**
> and where I can find more info about the differences between this two distributions? And finally do U think I should upgrade if current 8.1 version works perfect for me?


Diferences [http://www.ubuntu.com/getubuntu/releasenotes/904overview](http://www.ubuntu.com/getubuntu/releasenotes/904overview)

Upgrade Instructions [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by punia1979 on 2009-07-12
Thanx guys! ok I have decided to make that network upgrade for starters if everything is gona B ok I will make clean install (waiting for Ubuntu 9.04 CD) so lets say it is gona B in test state for another 3 weeks and after then will make clean install from original Ubuntu CD 

Regards ):P

---

### Post by punia1979 on 2009-07-14
ok I did system update, but my wireless is gone now :( I have atheros5007... when I am trying to reinstall my card when I trying to compile madwifi-ng-r2756+ar5007 I am getting this information... (how can I change path to my kernel?)

can't cd to /lib/modules/2.6.27-14-generic/build
Makefile.inc:66: *** /lib/modules/2.6.27-14-generic/build is missing, please set KERNELPATH.  Stop.

---

### Post by punia1979 on 2009-07-14
ok I have sorted this out on my own ;) I have edit menu.lst from /boot/grub and I swaped old path to kernel with the apropriate one ;)

---

### Post by CatKiller on 2009-07-14
> **DeMus said:**
> True, but upgrading is not as good as installing a new OS from the ground up, meaning wiping the drives clean and start all over. 

It's just as good. Same packages, same versions. I've been upgrading-in-place since Hoary, and in all that time the only thing that's been a problem that wouldn't have been with a fresh install was an experimental version of AWN that didn't get upgraded properly. Everything from the official repositories has been upgraded just fine.

Setting everything up the way it was can be a huge pain, the tweaks to this config file or that one that you just won't remember. The package management system is an amazing invention. It seems crazy that you'd want to just ignore it in favour of re-installing the OS every six months. If you're going to do that, you might as well be running an OS from the Pacific Northwest :)

---

### Post by pstep9407 on 2009-07-20
> **punia1979 said:**
> ok I have sorted this out on my own ;) I have edit menu.lst from /boot/grub and I swaped old path to kernel with the apropriate one ;)

Would you mind detailing this fix for the community? I am having this exact problem.

---

