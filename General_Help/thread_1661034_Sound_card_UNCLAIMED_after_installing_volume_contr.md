---
title: "Sound card UNCLAIMED after installing volume controll ap"
date: 2011-01-06
forum: General Help
---

### Post by hibob on 2011-01-06
Hi. I'm using Lucid laptop-edition on an HP dv6000 laptop. I wanted to tweak the bass-treble so I installed a few volume control apps from the software center (ALSA mixer, "Volume Control", JackEQ, maybe a few I don't remember).

They worked right after installation. but after restarting I have no sound. I can play with the volume all I want but I can't hear anything. When I open System/Preferences/Sound there are no devices in the hardware tab.

Here is what lshw says:
```

bob@bob-laptop:~$ sudo lshw -c sound
[sudo] password for bob: 
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f8400000-f8403fff
bob@bob-laptop:~$ 


```Please help me out.

---

### Post by hibob on 2011-01-07
Bump.

---

### Post by hibob on 2011-01-07
Solved by adding the device module from

```
lspci -v
```to /etc/modules

---

### Post by teejeh on 2012-12-04
Hibob,

I've had a similar problem with my HP DV-6-2144nr.
My question is what exactly you added to the etc/modules?
I'm running ubuntu 12.04, but the situation is very similar. Sound was working with minor issues(speakers weren't silenced when I plugged in headphones).  I installed alsamixer and it seems like the sound drivers got kicked out since I can only see "Dummy output" now.

Thanks

---

