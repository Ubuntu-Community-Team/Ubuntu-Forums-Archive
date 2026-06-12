---
title: "System Infomation"
date: 2011-07-04
forum: General Help
---

### Post by Affan.jau on 2011-07-04
I am new to Ubuntu. I am using Ubuntu 11.04.
I am trying to find out system information, like Processor Information, RAM and Graphics Card Info. 

What is the easiest way to find this information?

Thank you

---

### Post by CatKiller on 2011-07-04
**hardinfo** is quite nice. It's in the repositories.

---

### Post by haqking on 2011-07-04
try

sudo lshw -html > <yourfilename>.html

this will create a HTML doc of your hardware which you can view in a browser of your choice.

or just

saudo lshw

if you just want it on screen

---

### Post by Affan.jau on 2011-07-04
When i Search Hardinfo from Software Center it shows, System Profiler and Benchmark.

I tried lshw, but from it could not find anything about Display Driver..

---

### Post by haqking on 2011-07-04
> **Affan.jau said:**
> When i Search Hardinfo from Software Center it shows, System Profiler and Benchmark.

I tried lshw, but from it could not find anything about Display Driver..


mine is just after the network interfaces.

Just search it for diplay, i doubt very much it is omitted

---

### Post by Affan.jau on 2011-07-04
Thanx Haqking..
it shows as Display, with list of Product, version, and lot of other stuff.. But i Want to Know the SIZE, i dnt think it has that Info.


*-display:1 UNCLAIMED
             
description: Display controller
             
product: Mobile 915GM/GMS/910GML Express Graphics Controller          
vendor: Intel Corporation          
physical id: 2.1      
bus info: pci@0000:00:02.1          
version: 04         
width: 32 bits         
clock: 33MHz          
capabilities: pm cap_list        
configuration: latency=0       
resources: memory:24600000-2467ffff

---

### Post by Affan.jau on 2011-07-04
What i really want to know is the Size of the Graphics Card..

---

### Post by CatKiller on 2011-07-04
> **Affan.jau said:**
> When i Search Hardinfo from Software Center it shows, System Profiler and Benchmark.
That's the one.

---

