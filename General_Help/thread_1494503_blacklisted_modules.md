---
title: "blacklisted modules"
date: 2010-05-27
forum: General Help
---

### Post by plutoniumpenguin on 2010-05-27
Hello, I am in the process of attempting to get the nvidia-current drivers to work.  I read somewhere that it's a good idea to put the "nouveau" module in the blacklist.  So, I did so, but it evidently still loads?  I thought it was supposed to prevent it from loading!  Here's what I'm talking about:

---------
root@david-desktop:/home/david# grep nouveau /etc/modprobe.d/blacklist.conf
blacklist nouveau
root@david-desktop:/home/david# lsmod | grep nouveau
nouveau               515131  3 
ttm                    60815  1 nouveau
drm_kms_helper         30742  1 nouveau
drm                   198770  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
root@david-desktop:/home/david# 
--------

What do I do?  Do I need to blacklist all these modules, which seem to depend on nouveau, or what?

---

### Post by Ozymandias_117 on 2010-05-27
Just checking, have you rebooted since blacklisting the module..?

If so, what happens when you try to manually unload the module?
```
sudo modprobe -r nouveau
```

---

### Post by plutoniumpenguin on 2010-05-27
Thanks Ozymandias.  Unfortunately, yes, I have have rebooted since blacklisting the module, so the problem is not that simple.  Here's the output from that command:

--------
root@david-desktop:/home/david# modprobe -r nouveau
FATAL: Module nouveau is in use.
root@david-desktop:/home/david# 
--------

Actually, the lsmod command says that nouveau is used by "3" (processes?  modules?  i don't know what that number actually refers to), but it remains silent as far as the details go (i.e. it doesn't explicitly say what is using it), although I'm guessing it's xserver/gnome or something.

---

### Post by rnerwein on 2010-05-27
> **plutoniumpenguin said:**
> Hello, I am in the process of attempting to get the nvidia-current drivers to work.  I read somewhere that it's a good idea to put the "nouveau" module in the blacklist.  So, I did so, but it evidently still loads?  I thought it was supposed to prevent it from loading!  Here's what I'm talking about:

---------
root@david-desktop:/home/david# grep nouveau /etc/modprobe.d/blacklist.conf
blacklist nouveau
root@david-desktop:/home/david# lsmod | grep nouveau
nouveau               515131  3 
ttm                    60815  1 nouveau
drm_kms_helper         30742  1 nouveau
drm                   198770  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
root@david-desktop:/home/david# 
--------

What do I do?  Do I need to blacklist all these modules, which seem to depend on nouveau, or what?
hi
i am using the nvidia driver too.
in my /etc/modprobe.d/blacklist.conf i even can't find the nouveau ---> but there is another file inside that
directory: 
[COLOR=Blue]nvidia-graphics-drivers.conf:blacklist nouveau
nvidia-graphics-drivers.conf:blacklist lbm-nouveau[/COLOR]

and there i can find the blacklisted driver.

ciao

---

### Post by Ozymandias_117 on 2010-05-27
> **plutoniumpenguin said:**
> Actually, the lsmod command says that nouveau is used by "3" (processes?  modules?  i don't know what that number actually refers to), but it remains silent as far as the details go (i.e. it doesn't explicitly say what is using it), although I'm guessing it's xserver/gnome or something.

> ---------
root@david-desktop:/home/david# lsmod | grep nouveau
nouveau 515131 3 

**ttm** 60815 1 **nouveau**

**drm_kms_helper** 30742 1 **nouveau**

**drm** 198770 3 **nouveau**,ttm,drm_kms_helper

**i2c_algo_bit** 6024 1 **nouveau**
root@david-desktop:/home/david# 
--------

It says it's used by three processes, but shows four. The fourth column is where it tells you what that module depends on, so, the items that use nouveau are ttm, drm_kms_helper, drm, and i2c_algo_bit.

---

### Post by plutoniumpenguin on 2010-05-27
OK, I checked my modprobe.d directory, and it also has an nvidia-graphics-drivers.conf file, which reads

------
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
------

So, I guess my adding "blacklist nouveau" to blacklist.conf was redundant.  But that still doesn't explain why the module keeps getting loaded.

Since 4 other modules evidently "make use of" nouveau, does that mean that I have to blacklist these other modules as well, before nouveau stops loading, or what?  Actually, I would assume that you'd simply need to use instead another module that can provide the same functionality as nouveau, but clearly the nvidia driver should fit this category and for some reason it isn't being loaded (well, from looking at the logs, it seems like it's loaded and then immediately unloaded).

---

### Post by rnerwein on 2010-05-28
hi
may this can help you too. i found another blacklist entry in /etc/modprobe.d/blacklist-framebuffer.conf
the entry is: [COLOR=Blue]blacklist nvidiafb[/COLOR]

on the other side - the nvidia stuff on my box ( lucid lynx ) works out of the box.
ciao

---

### Post by Mario13 on 2010-05-29
I had the same problem.

It appears that the driver **nouveau.ko** is loaded very early in the boot proccess, this way it can provide text modes with more than the standard 80x25 characters.

In order to prevent **nouveau.ko** to be loaded, I blacklisted it in /etc/modprobe.d/blacklist.conf, but also renamed this file:
/lib/modules/2.6.32-22-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
to nouveau.ko.001 (or whatever other name)
You can also delete or move this file.

After a reboot I was able to install de binary Nvidia driver from its installer.

---

