---
title: "How to create backup ISO of my system"
date: 2010-09-12
forum: General Help
---

### Post by anirudhtomer on 2010-09-12
Hi everyone,

I regularly update the softwares on ubuntu and I do not want to lose them in case my hard disk crashes. 
So I was wondering how could I make the ISO of my ubuntu which is there on my machine so that even if everything crashes I have a safe ISO image of my ubuntu which I can use later. This way I will be having all those installed packages safe. 
The super ubuntu ([http://hacktolive.org/wiki/Super_OS](http://hacktolive.org/wiki/Super_OS)) ISO comes with many packages installed in it. So like super OS I want to have an ISO with all of my packages Pre-installed in it & when I install from it I get everything ready & cooked.

Can anyone help me out on this issue?

---

### Post by jmszr on 2010-09-12
anirudhtomer,

You can use remastersys. Here are a few links for you: [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html) and: [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) also: [http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

### Post by coffeecat on 2010-09-12
You don't necessarily need to make an ISO specifically, just an image for restoring a system. Have a look at clonezilla:

[http://clonezilla.org/](http://clonezilla.org/)

I've seen good reports of it but I've never used it. I use the crude but effective way of running tar from a live CD (or from another Linux installation on another partition) to image my root partition. The main disadvantage of that is that you will have to edit /etc/fstab and repair grub after a restore, but I'm used to it. I've used it for several years for cloning installations set up the way I like them, or restoring ones I've - ahem - broken. :wink:

---

### Post by anirudhtomer on 2010-09-12
Thanks for solving my problem. There is one more solution to this problem at [http://uck.sourceforge.net/](http://uck.sourceforge.net/)

I am going to use remastersys.

Thanks to all.):P

---

