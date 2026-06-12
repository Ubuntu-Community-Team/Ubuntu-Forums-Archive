---
title: "installing grafic drivers"
date: 2012-05-20
forum: General Help
---

### Post by ajdinm on 2012-05-20
Hello :D
I've installed ubuntu on my pc (choosing to delete everything before; including my win7 and all drivers)
this new os doesn't recognize my grapic card at all, and i dont know how to install it's drivers.
also, at terminal, when i try to write password, i can't. when i type if just freze and says sorry, wrong informatior, or something like that.
How to fix those issues, especially one with GFX card?
Thanks a lot :D

---

### Post by Cheesemill on 2012-05-20
What graphics card do you have?

Also when you enter your password in a terminal you don't see any feedback, that's normal.
Just type your password as usual and hit enter.

---

### Post by jocko on 2012-05-20
If you provide the output from this command we will see exactly what graphics card you have and which driver it currently uses:
```
sudo lshw -C display
```

---

### Post by celldweller1591 on 2012-05-20
I think [this post]("http://www.linoob.com/2011/04/installing-hardware-drivers-in-ubuntu/") might solve your problem. just go through this guide and you will be fine.

---

### Post by Eagle7261 on 2012-05-20
> **jocko said:**
> If you provide the output from this command we will see exactly what graphics card you have and which driver it currently uses:
```
sudo lshw -C display
```

the OP should know, this will work, but there may be a delay,
at least there is on my machine
ex:
mine shows "PCI (sysfs)" with no username prompt
then after 30 sec or so, the full info pops up & the prompt returns

though it may be because I'm currently transcoding an .avi to .VOB
in the backround, so I'm prob not running at max speed

UPDATE:
transcode finished, still has a delay

Have you checked 'additional drivers' in the hardware section of 'system settings'?
that's what I had to do on mine, choose/activate the drivers for my gfx & lan cards

---

### Post by ajdinm on 2012-05-20
Here is what i get after typing in the command.
> *-display               
       description: VGA compatible controller
       product: Redwood [Radeon HD 5670]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:46 memory:e0000000-efffffff memory:dffc0000-dffdffff ioport:e000(size=256) memory:dffa0000-dffbffff
Today I was doing something around drivers and i think i've found it. If i instaled it well (hopefully u can see via this info) this thread can be closed. Thanks :D

---

### Post by jocko on 2012-05-21
> **ajdinm said:**
> Here is what i get after typing in the command.
*-display               
       description: VGA compatible controller
       product: Redwood [Radeon HD 5670]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: **[COLOR=Red]driver=fglrx_pci[/COLOR]** latency=0
       resources: irq:46 memory:e0000000-efffffff memory:dffc0000-dffdffff ioport:e000(size=256) memory:dffa0000-dffbffff
Today I was doing something around drivers and i think i've found it. If i instaled it well (hopefully u can see via this info) this thread can be closed. Thanks :D
Looks like you have the proprietary ati driver (fglrx) installed and working.

---

### Post by ajdinm on 2012-05-21
Great, thanks :D

---

