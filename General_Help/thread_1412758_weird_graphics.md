---
title: "weird graphics"
date: 2010-02-21
forum: General Help
---

### Post by linux_noob0 on 2010-02-21
i'm having problems with weird graphics on ubuntu ( on the login screen you can see the gradient split into layers like a low-quality gif image.. ). on my old laptop everything works looks smooth, but here it's buggy. does it have anything to do with my graphics drivers ( which are nvidia quadro NVS 3100M, i can't seem to find the original drivers on nvidia's site.. thanks!

---

### Post by quixote on 2010-02-23
Yup, it's defaulting to the lowest grade driver because it doesn't have the right one for your nvidia chip.  Nvidia makes excellent graphics hardware, but they're very stupidly cranky about linux, so they have no drivers for our systems.  

There are nvidia drivers you can install from synaptic (nvidia-glx-something?) (type "nvidia" in the search box), but there are also more up-to-date ones in an experimental repository.  To add that, you'd type in a terminal:```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```Then you could start synaptic, reload repositories, and search for everything "nvidia" again.  There should be the new & improved 190.42 driver listed now.

(Info from here: [http://www.sizzledcore.com/2009/11/02/nvidia-graphics-drivers-19042-for-ubuntu-910/](http://www.sizzledcore.com/2009/11/02/nvidia-graphics-drivers-19042-for-ubuntu-910/), and here: [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html#more-2454](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html#more-2454)  That last one has instructions for the specific packages needed. )

---

