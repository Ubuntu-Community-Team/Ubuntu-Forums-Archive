---
title: "Nouveau on 11.10"
date: 2012-03-11
forum: General Help
---

### Post by tsumaru on 2012-03-11
Hi all, 

I have a netbook that I have just installed clean 11.10 on. Out of the box it seemed to work great! All the desktop effects work fine.

I have only one concern though, since its been on the cooling fan has not stopped and the device is VERY hot. I have checked cpu freq and its down to 800mhz from 1.6ghz so i doubt its the cpu generating the heat.

lm-sensors reports ~39C for CPU and 64C for nouveau-pci

After a bit of digging it seems that nouveau is a new driver that is being used for Nvidia cards (Mine is an ION LE)

I have tried to install the nvidia drivers from nvidia.com in the hopes that it dynamically adjusts GPU clock thus reducing heat and power consumption but ive hit a bit of a wall.

I cant seem to disable nouveau!

I have added it to my blacklist file: /etc/modprobe.d/blacklist.conf 

```
blacklist nouveau
```

but every time i boot it is always loaded. This is stopping the nvidia drivers from being used.

Can anyone suggest how i can disable nouveau so that i can test the nvidia drivers to see if they work better at reducing power usage/heat?

**EDIT**

It also seems that nouveau does not yet support VDPAU which means that i am currently unable to watch 720p video on my netbook.

The main reason for its use is for watching things whilst travelling - Anyone got any thoughts?

---

