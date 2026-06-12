---
title: "Cant find my graphic's card?"
date: 2012-04-06
forum: General Help
---

### Post by Mindrop on 2012-04-06
I am using a 20'' LCD screen so I noticed right away something was majorly off. I can only have a 800x600 or 640x480 resolution and I also can not have any visual effects either. I just installed Ubuntu, but i cant recognize my graphics card. It does recognize my wireless card though. When I click on drivers, it fails to find any. 

Its ubuntu 10.04 64 bit 

Any help?

---

### Post by RJARRRPCGP on 2012-04-06
What graphics hardware do you have? 

Sounds like it may be later than Oneiric Ocelot, thus, may have to wait for Precise Pangolin.

---

### Post by Mindrop on 2012-04-06
Geforce GTS 450

[http://www.geforce.com/hardware/desktop-gpus/geforce-gts-450](http://www.geforce.com/hardware/desktop-gpus/geforce-gts-450)

---

### Post by Yellow Pasque on 2012-04-06
nvidia-graphics-drivers package from here should work: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)

---

### Post by Mindrop on 2012-04-06
Okay, now I have a new question. 
> 
Replace ppa:user/ppa-name with the PPA's location that you       noted above.     

URL to install directions is here:

[https://launchpad.net/+help-soyuz/ppa-sources-list.html](https://launchpad.net/+help-soyuz/ppa-sources-list.html)

---

### Post by Yellow Pasque on 2012-04-06
????????

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

---

