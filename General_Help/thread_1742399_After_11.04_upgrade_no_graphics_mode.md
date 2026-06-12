---
title: "After 11.04 upgrade no graphics mode"
date: 2011-04-28
forum: General Help
---

### Post by kkruecke on 2011-04-28
I upgrade from 10.10 to 11.04. Now Ubuntu boots into command line mode because, according to the logs, my Nvidia graphics driver won't load. 

/usr/lib/xorg/extra-module/nvidia_drv.so is the location of the driver.

How do I fix this, or at least come up in graphics mode, so I can access the internet? I had to boot into Windows to post this.

---

### Post by kkruecke on 2011-04-28
After booting into Windows, I could reboot into Ubuntu and come up in graphics mode. Strange.

I then installed nvidia-current. At least x comes up now.

---

### Post by williejones on 2011-04-28
Probably just needed a reboot?

---

### Post by kkruecke on 2011-04-28
Yes, but once X came up, I also had to install

  nvidia-current

which involved first removing the broken nvida driver, nvidia-180-modalias.

---

### Post by williejones on 2011-04-28
> **kkruecke said:**
> Yes, but once X came up, I also had to install

  nvidia-current

which involved first removing the broken nvida driver, nvidia-180-modalias.


Thanks for posting your fix so others may use it.  You should mark this as solved for 
future searches to help others.

---

