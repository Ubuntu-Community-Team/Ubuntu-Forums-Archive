---
title: "Package Broken"
date: 2009-08-03
forum: General Help
---

### Post by iqbalsound on 2009-08-03
Hi to all i am new bie here .. well i am facing the below problem which i tried to fix with Synaptic > Edit> Fix broken package but noting happen kindly help me to evalute te problem :(

**[COLOR=Red]E: /var/cache/apt/archives/linux-image-2.6.28-14-generic_2.6.28-14.47_i386.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.28-14-generic/kernel/drivers/net/wireless/airo.ko')[/COLOR]**

---

### Post by nothingspecial on 2009-08-03
Try ```
sudo apt-get install -f

```
Then 

```
sudo apt-get clean
```

---

