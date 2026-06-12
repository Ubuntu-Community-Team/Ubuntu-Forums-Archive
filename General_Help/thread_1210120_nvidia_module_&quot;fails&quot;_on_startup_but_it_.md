---
title: "nvidia module &quot;fails&quot; on startup but it works"
date: 2009-07-11
forum: General Help
---

### Post by JDShu on 2009-07-11
Not a life or death problem, but when I boot, I get the message :

 *nvidia (180.44) ...     [fail]

But when my desktop comes up everything is working fine and I'm using the nvidia driver that I installed manually (185.18.14)

Why is it trying to load a module that shouldn't be there and how can I stop it?

Thank you in advance.

---

### Post by QIII on 2009-07-11
Could you post what you did to manually install the new driver?

You basically need to retrace those steps backwards with the old driver ...

Using "remove --purge <whatevertheolddriveris>" in the terminal.

---

### Post by JDShu on 2009-07-11
Thanks for the quick response.

I first tried to install the default driver through the Hardware Drivers interface, but it didn't work probably because I updated my kernel to 2.6.30. So I downloaded the nvidia driver from the website (NVIDIA-Linux-x86_64-185.18.14-pkg2.run) and ran it. Magically, it seems to have worked. I just have this odd nonexistant module on my system, maybe because of my attempt with Hardware Drivers.

---

### Post by JDShu on 2009-07-11
Awesome, I got it working. Thanks alot QIII for the insight. I ended up running:

sudo apt-get purge nvidia*

to get rid of the default drivers and then running the new driver script again to compile the new module.

---

