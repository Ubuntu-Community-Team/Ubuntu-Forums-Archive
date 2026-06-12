---
title: "Problem with graphics?"
date: 2010-12-02
forum: General Help
---

### Post by chippy_250 on 2010-12-02
Since becoming a Ubuntu user my PC can't seem to play any graphics i.e. every time the screen saver is about to kick in the screen goes black and logs me out as a user. (Which loses everything I've been doing.)
Also, every time I try to run a program under Wine the screen goes distorted (icons go really big and blurry), then it goes black and logs me out as a user. 

Is this a graphics card issue or some sort of other problem?

Please help me!

---

### Post by karthick87 on 2010-12-02
Can you post the output of

```
sudo lshw -C display
```

---

### Post by chippy_250 on 2010-12-04
> **karthick87 said:**
> Can you post the output of

```
sudo lshw -C display
```
What does this do?

---

### Post by DeMus on 2010-12-04
> **chippy_250 said:**
> What does this do?

lshw stands for list hardware
display is a sort of filter which only shows you info about your graphics card
Don't worry, this code does not destroy anything. I just tried it and I get this:

```
sudo lshw -C display
[sudo] password for ****: 
  *-display               
       description: VGA compatible controller
       product: G86 [GeForce 8500 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:cc00(size=128) memory:fe8e0000-fe8fffff
```

---

### Post by chippy_250 on 2010-12-04
*-display UNCLAIMED     
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=32 maxlatency=255 mingnt=4
       resources: memory:ed000000-ed07ffff memory:e0000000-e7ffffff memory:ec000000-ec00ffff


So is this graphics card not good enough to run Ubuntu or something?

---

