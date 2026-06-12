---
title: "Ubuntu won't display monitor"
date: 2011-03-18
forum: General Help
---

### Post by dangfrick on 2011-03-18
I am having trouble trying to get my viewsonic VX2739wm 27" monitor to display while using ubuntu. 

I have two monitors, and under monitor preferences it is detecting both monitors, and I have both set to be turned on. It is acting like the monitor is turned on, I can move my mouse and drag windows onto the other screen, but it is completely black and won't turn on. 

By turn on, I mean it is acting like it is in sleep once I choose to boot ubuntu instead of windows 7, and it will not come out of sleep.

I tried to find an ubuntu driver but I couldn't find one. The monitor works find while using Windows 7. Any ideas?

---

### Post by dangfrick on 2011-03-19
bump?

---

### Post by dangfrick on 2011-03-23
Anyone?

---

### Post by dangfrick on 2011-03-23
I will send you $10 via paypal if you can solve this problem

---

### Post by PCNetSpec on 2011-03-23
Which graphics card do you have and which drivers are you using for it?

sudo lshw -C display

Will tell you.

And which version of Ubuntu

---

### Post by dangfrick on 2011-03-23
Ubuntu 10.10
I used the windows installer to install it

sudo lshw -C display

PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: G94 [GeForce 9600 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:cc000000-ccffffff memory:b0000000-bfffffff memory:ca000000-cbffffff ioport:9c00(size=128) memory:cd000000-cd07ffff

---

### Post by PCNetSpec on 2011-03-23
Try installing the NVIDIA drivers rather than nouveau...

System > Administration > Additional Drivers

---

### Post by dangfrick on 2011-03-23
Alright sweet, got it working after updating the drivers and restarting the x server like 10 times lol. you can pm me that paypal info.

---

### Post by PCNetSpec on 2011-03-23
Heh, I hadn't spotted that... you're OK no need ;)

---

