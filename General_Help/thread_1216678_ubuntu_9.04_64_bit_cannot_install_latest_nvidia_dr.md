---
title: "ubuntu 9.04 64 bit cannot install latest nvidia driver"
date: 2009-07-18
forum: General Help
---

### Post by serious7 on 2009-07-18
As thread title states, I CANNOT install the latest 64 bit drivers from Nvidia. I downloaded it, I turned off x-server, i installed it on command line and when I restart x-server it will list a bunch of errors like kernal cannot be loaded blablabla. Screen flickered a lot and I had to just re-install ubuntu. Now I'm on a fresh install AGAIN, and I'm afraid of trying to install the latest drivers. Can someone help me? I'm new to linux.

---

### Post by Tman5293 on 2009-07-18
Don't use the command line. Try going to: System>Administration>Hardware Drivers
Try installing from there.

---

### Post by serious7 on 2009-07-18
> **Tman5293 said:**
> Don't use the command line. Try going to: System>Administration>Hardware Drivers
Try installing from there.

It's not the latest driver. I kinda want to go through the command line to learn linux. I'm using ubuntu just to learn linux ...

---

### Post by serious7 on 2009-07-18
bump

---

### Post by Praill on 2009-07-18
Installing the latest drivers manually can be a pain. 
I have had luck in the past with a nice little tool called EnvyNG however. Here are installation instructions for EnvyNG:
[http://www.albertomilone.com/envyngfaq.html#A]("http://www.albertomilone.com/envyngfaq.html#A")

I am not guaranteeing envyng will work for you. It has worked 95% of the time for me in the past however so it is a good option. 
If this doesn't work you might just have to bite the bullet and go with v180 that's officially supported by Ubuntu 9.10 in the Restricted Hardware module.

---

### Post by serious7 on 2009-07-18
nvm guys. I got it running this time. I think it failed the first time because I had the official driver from ubuntu installed and that caused a conflict. stupid drivers. They should make ubuntu more user friendly for newbies like me.

---

### Post by Praill on 2009-07-18
Glad you got it working. You might want to reconsider this approach as every time you upgrade kernels you're going to have to go through the same procedure.

Personally, I would run with the latest driver for a few weeks, then maybe try the driver supported by the Restricted Hardware module and if you don't notice any difference between the two go with the supported one. 

Any driver installed through the Restricted Hardware module will reinstall itself on kernel upgrades. A very nice feature (trust me).

---

