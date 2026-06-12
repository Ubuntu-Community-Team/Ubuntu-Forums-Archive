---
title: "Riva TNT2 Driver"
date: 2009-06-26
forum: General Help
---

### Post by CyclicUniverse on 2009-06-26
Hey all,

I left a thread a day or two ago under "hardware & laptops" and I got no replies...

I'm having trouble getting/installing the driver for my Gigabyte GA-660 Plus 32mb (nVidia Riva TNT2/TNT2 Pro chipset) for Ubuntu 9.04

I have found a thread saying there are new nVidia drivers available, but they are only for the newer graphic cards (GeForce).

The thread also included the following:

> log into terminal

cd desktop/

sudo /etc/init.d/gdm stop

sudo sh ./Nxxx.run

sudo reboot

I have done so after downloading the "NVIDIA-Linux--x86-71.86.09-pkg1.run" file from the nVidia webpage.

I followed the instructions and then rebooted.  When logging in (GNOME) I went to the Display Settings and was given the option: 

> "It appears that your graphics driver does not support the extensions to use this tool"

I am clueless and also very new to Ubuntu/Linux...

Please could someone help me out??


p.s. my system specs are

AMD Athlon 1.7ghz
0.97g ram
40gb maxtor hdd (Windows XP SP3)
120gb seagate hdd (Ubuntu 9.04 + updates)
Gigabyte GA-660 Plus 32mb

---

### Post by Soul-Sing on 2009-06-26
There is no driver available via: system: hardware drivers?
Some threads shows that you need the: nvidia-glx-71 driver....

---

### Post by CyclicUniverse on 2009-06-26
Ok..  Thanx

So how do I go about solving my problem??  I really love using Ubuntu, but at the moment my screen resolution is not 800x600 and I can't set it higher :(

Would a repository @ [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html) help me in any way?

---

### Post by CyclicUniverse on 2009-06-26
forgot to add that I checked under  System >Hardware Drivers  and the list is completely empty...

what does this mean?

---

### Post by CyclicUniverse on 2009-06-27
hey,

my "Hardware Drivers" window says:

No Propietary Drivers are in use on this system

wtf??!?!

---

### Post by dcstar on 2009-06-27
> **CyclicUniverse said:**
> Hey all,

I left a thread a day or two ago under "hardware & laptops" and I got no replies...

I'm having trouble getting/installing the driver for my Gigabyte GA-660 Plus 32mb (nVidia Riva TNT2/TNT2 Pro chipset) for Ubuntu 9.04
.......

Old Nvidia video chipsets are not supported by Ubuntu past version 8.04 (maybe earlier?) - you can still install an older Ubuntu LTS version that will support your hardware and remain supported for a few years yet.

---

### Post by CyclicUniverse on 2009-06-29
well, that's not cool :(
 
you mean to tell me that theres no way for me to make my Ubuntu look and feel abit better other than buying a new graphics card??

---

### Post by andriansah on 2009-07-05
> **CyclicUniverse said:**
> well, that's not cool :(
 
you mean to tell me that theres no way for me to make my Ubuntu look and feel abit better other than buying a new graphics card??


Is there an answer for this?, it's been 3 weeks since my upgrade to jaunty but I still can change to 1024x768, that's all i need, I don't need compiz and friend

---

