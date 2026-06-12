---
title: "How do I prevent  modules from loading?"
date: 2011-05-21
forum: General Help
---

### Post by 5149.5 on 2011-05-21
I am running 11.04 and would like to stop the loading of the parport and lp modules. I put entries in the /etc/modprobe.d/blacklist.conf file and ran update-initramfs -u. After a reboot lsmod shows both modules as being loaded.

---

### Post by wildmanne39 on 2011-05-21
> **5149.5 said:**
> I am running 11.04 and would like to stop the loading of the parport and lp modules. I put entries in the /etc/modprobe.d/blacklist.conf file and ran update-initramfs -u. After a reboot lsmod shows both modules as being loaded.
Hi, you can use ```
sudo modprobe -r <name of module>
```
to remove it.

---

### Post by 5149.5 on 2011-05-21
> **wildmanne39 said:**
> Hi, you can use ```
sudo modprobe -r <name of module>
```to remove it.

That works fine but I want to prevent them from loading at boot.

---

### Post by 5149.5 on 2011-05-22
I figured it out. There was a line in /etc/modules tht was overriding the blacklist entry for the lp module. I guess the parport module was being loaded as a dependency for the lp module. When I commented out the the lp line in /etc/modules the lp and parport modules disappeared from the lsmod listing after an update-initramfs and a boot.

---

### Post by wildmanne39 on 2011-05-22
> **5149.5 said:**
> I figured it out. There was a line in /etc/modules tht was overriding the blacklist entry for the lp module. I guess the parport module was being loaded as a dependency for the lp module. When I commented out the the lp line in /etc/modules the lp and parport modules disappeared from the lsmod listing after an update-initramfs and a boot.

Hi, thats good I was going to mention commenting it out but I figured you had tried that.):P

---

