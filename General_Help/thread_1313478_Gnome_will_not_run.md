---
title: "Gnome will not run"
date: 2009-11-03
forum: General Help
---

### Post by thegodsquirrel on 2009-11-03
Upon reboot gnome will not start due to resolution issues.  However once back in the console you can manually start XFCE. On NVIDIA, which leads me to believe that it is not a video driver issue.  gnome will not start on vesa or a lower resolution set in xorg.conf.  

This is the only error I get when starting gnome:

(EE) Failed to load Module "Type1" (Module does not exist)

(EE) Failed to load Module "freetype" (Module does not exist)

Helps

---

### Post by lidex on 2009-11-03
What distro and version are you using? Have you tried reconfiguring Xorg? What video driver is installed? Can you post contents of xorg.conf please?

Post output of this command:
```
sudo lshw -C video
```


Try this in a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by thegodsquirrel on 2009-11-05
bump

---

### Post by thegodsquirrel on 2009-11-05
oot@euclid-laptop:/root# sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: C51 [GeForce Go 6100]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:17 memory:b2000000-b2ffffff memory:c0000000-cfffffff(prefetchable) memory:b1000000-b1ffffff memory:80000000-8001ffff(prefetchable)
root@euclid-laptop:/root# ^C
root@euclid-laptop:/root#

---

### Post by Tony Newton on 2009-11-23
Same problem. Gnome stopped working. And I cant figure out why or how to fix it. This OS is really starting to annoy me. For some thing that is trumpeted as easy to use and modern it sure seems flaky, difficult to work with and bug ridden to me.

---

