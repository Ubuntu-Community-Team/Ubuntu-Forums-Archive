---
title: "Raid 1 on Raid 0 or LVM - Startup"
date: 2011-05-13
forum: General Help
---

### Post by wimmelis on 2011-05-13
Dear all, 


On my machine, I set up a software RAID 1. Since I need to combine a few partitions on different drives for one part of my RAID 1, I initially went for a RAID 0 approach to combine these partitions.  
When booting up my system, the RAID 0 and RAID 1 involved would never boot properly (degraded, not started, ...), and I would always have to rectify it manually after boot. 
I searched for a solution, and could not quite find a proper solution, but had the impression that using an LVM to combine would solve the problem. However, this approach seems to have a similar problem of not booting properly. 
Anyone who can help me get this to work properly when it comes to booting ?


Thanks, 

WM

---

### Post by wimmelis on 2011-05-17
Dear all, 


Problem seems to be solved now. In the file mdadm.conf, the RAID 1 array was not presented. Eventhough, it was not there, it seems that during boot time the computer still tried to build the array, hence I ended up with quite some arrays named md_dx, which were all useless. By adding the LVM volume as a DEVICE in that file, and then properly defining the devices that make up the array, it seemed to know what to do when booting. 

So at the top of the file, I added:
DEVICE /dev/sdx* (Repeat for all devices that you use)
DEVICE /dev/mapper/LVM_Volume

and then later on in the file:
ARRAY /dev/mdx level=raid1 num-devices=2 devices=/dev/mapper/LVM_Volume,/d
ev/sdxx

Hope this helps others who struggle with this situation. 


Regards, 

WM

---

