---
title: "Cant get on Ubuntu since I switched to kdm"
date: 2009-12-03
forum: General Help
---

### Post by xxhopingtearsxx on 2009-12-03
Yesterday, I was looking for a way to shut down my computer from Kubuntu since the only option I get is "Switch User" and "Logout" and "Sleep" etc.. so I found a message board that told me to do 

```
sudo dpkg-reconfigure kdm
```
and select kdm. I did that. I rebooted. I tried getting back on and I see the Kubuntu splash screen and then a black blank screen.. So now I'm on Windows 7 Release Candidate again. Great thing I didn't remove Windows or I'd have to reinstall Ubuntu or ask for help on my Iphone's Safari.

Please help. I have a live cd and on the live CD I did "sudo dpkg-reconfigure gdm" on Terminal thinking it would work, and I rebooted and nothing changed.

---

### Post by DiodePorridge51b on 2009-12-08
Good day to ye

Something similar happened to me - this problem seems to be the result of an interaction between Ubuntu GDM startup scripts and other display managers. See the below list of links for suggestions of workarounds. There's also a proposed update in the karmic-proposed repository that seems to do some of the job (for GDM, I think).

[http://ubuntuforums.org/showthread.php?t=1343012&page=2](http://ubuntuforums.org/showthread.php?t=1343012&page=2)
[http://ubuntuforums.org/showthread.php?t=1343261&page=5](http://ubuntuforums.org/showthread.php?t=1343261&page=5)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483)

Peace

---

### Post by DiodePorridge51b on 2009-12-08
Also,

You probably don't need the Live CD to deal with this - you can get to a login prompt by using the boot manager (presumably you are using "GRUB") and "e"diting the kernel command so that it contains "rw init=/bin/bash" - this should be enough to implement some of the fixes mentioned in the links.

Peace

---

