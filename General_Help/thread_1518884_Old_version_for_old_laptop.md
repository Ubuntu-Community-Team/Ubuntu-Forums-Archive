---
title: "Old version for old laptop"
date: 2010-06-27
forum: General Help
---

### Post by sxmaxchine on 2010-06-27
Hello i am looking for an ubuntu distro for my sisters old laptop. It has:
192mb RAM
50gb HDD
1.6ghz celeron M
64mb ati radeon xpress 200 (not positive wil verify this)

What do you think the best ubuntu distro for this laptop.

---

### Post by dragos240 on 2010-06-27
You won't get ubuntu on that. Try another lighter distro, ubuntu is too heavy for that type of system.

---

### Post by sxmaxchine on 2010-06-27
Thanks for the reply, and i will now ask another question:
    what lightweight distro can i use that has an installer that allows me to keep my current windows partition. (I already tried arch linux and it wouldnt work)

---

### Post by snowpine on 2010-06-27
> **sxmaxchine said:**
> Thanks for the reply, and i will now ask another question:
    what lightweight distro can i use that has an installer that allows me to keep my current windows partition. (I already tried arch linux and it wouldnt work)

Nearly all Linux distros (including Arch) will allow you to dual boot with your current Windows install.

[http://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot](http://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot)

Arch is a good choice, maybe a bit "advanced" for some users. I would also recommend test driving Lubuntu, CrunchBang, Antix, Puppy, and SliTaz. There are a lot of good "lightweight" distros these days, sometimes the decision comes down to trying a few and picking the one that runs best on your specific hardware.

---

### Post by dragos240 on 2010-06-27
> **sxmaxchine said:**
> Thanks for the reply, and i will now ask another question:
    what lightweight distro can i use that has an installer that allows me to keep my current windows partition. (I already tried arch linux and it wouldnt work)

Arch is for i686 computers, yours looks like an i586 at best. You should look into partitioning. All distros will allow you to keep windows, you just have to learn to partition. A good distro is debian, ubuntu is based on debian! Try something like LXDE with debian, it's a bit harder to install, but it *should* work.

---

### Post by ford074 on 2010-06-27
There is a Puppy Linux version of Ubuntu [http://puppylinux.org/news/releases/lucid-puppy-from-woof-and-ubuntu-lucid-lynx-/]("http://puppylinux.org/news/releases/lucid-puppy-from-woof-and-ubuntu-lucid-lynx-/")

You might take a look at that.
Very fast.
It can be run as a live cd or installed on the hdd.

---

### Post by sxmaxchine on 2010-06-27
I had archbang working fine on the machina and i got to the installer of arch linux but then decided it might be a bit complex for the rest of my family.

Puppy is a good distro and have considered it i cant find something else.

And i did get ubuntu warty to work perfectly from live cd.

---

### Post by snowpine on 2010-06-27
It may seem logical to say "the computer is old, therefore I should use an older distro" but I disagree with this logic. :(

Older releases (like warty) are no longer supported with bug fixes, security patches, current applications, etc. You're better off using a modern lightweight distro IMHO; there have been huge advances in the last couple of years, LXDE project for example.

---

### Post by sxmaxchine on 2010-06-27
Thanks for all the responses i am going to try lubuntu out

---

### Post by dzon65 on 2010-06-27
Give slitaz a try,downloading,burning and installing will take 20 minutes.Lubuntu will prove to be slow on those specs.

---

### Post by sxmaxchine on 2010-06-27
Thanks i will definetely try it out

And thanks to everyone for the help.

---

### Post by dzon65 on 2010-06-27
The xvesa version just works out of the box,the xorg version needs a xorg conf edit.So all depends on your screen res.If it's 1024X768,take the xvesa version.Both iso's are <30mb.

---

### Post by cascade9 on 2010-06-27
> **dragos240 said:**
> Arch is for i686 computers, yours looks like an i586 at best. You should look into partitioning. All distros will allow you to keep windows, you just have to learn to partition. A good distro is debian, ubuntu is based on debian! Try something like LXDE with debian, it's a bit harder to install, but it *should* work.

Arch is i686, and so is that celeron. The last of the i586 CPUs were the Intel Pentium MMXs, AMD K6s and the Cyrix M2s. 

> **snowpine said:**
> It may seem logical to say "the computer is old, therefore I should use an older distro" but I disagree with this logic. :(

Older releases (like warty) are no longer supported with bug fixes, security patches, current applications, etc. You're better off using a modern lightweight distro IMHO; there have been huge advances in the last couple of years, LXDE project for example.

+1. 

But I'm not overly impressed with LXDE, from my playing with it LXDE seems to be only a few MB lighter than Xfce.

---

