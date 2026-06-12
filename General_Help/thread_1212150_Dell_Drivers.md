---
title: "Dell Drivers"
date: 2009-07-13
forum: General Help
---

### Post by LazyLlama on 2009-07-13
Hello Ubuntuians! I've got a bit of a problem, as usual. Recently I got a Dell Studio 1555, which worked perfectly. I loaded up Ubuntu and everything was just fine, sound and picture. Awesome. But then windows crashed, not sure why - took a while to fix, and when I got it working all the drivers were gone. So I painfully loaded them all up which took a couple hours.
 However, when loading Ubuntu back up, it was (and still is) all wrong! No sound, and the picture is centered with black sides.
 I'm guessing its because I have none of the drivers.
It would be a great help if someone could point me into the direction of these drivers - or give me some direct links!
I do still have the disk with all the drivers, and although I know its for windows, could I use it with ubuntu

Any Help Will be Much Appreciated!
-LazyLlama

---

### Post by northern lights on 2009-07-13
Please post the outputs of ```
sudo lshw -C display
```and```
sudo lshw -C multimedia
```

---

### Post by LazyLlama on 2009-07-13
For the first I got: 

 *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

And second I got:

*-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

The Keyboard and mouse also seems to be acting up - I'm not sure whats happening there or if it is connected to the same problem...

---

### Post by LazyLlama on 2009-07-13
Bump + Update

Sorry - I know it sucks when people bump :P

But I'd like to say I managed to get the screen res back to how it should be - still a problem with the sound and mouse though.

Thanks Again!
-LazyLlama

---

### Post by GCoffee on 2009-07-13
Do you use a touchpad or USB mouse?

---

### Post by LazyLlama on 2009-07-14
USB mouse most of the time - but sometimes I will use the touchpad.
Its only a cheap thing, doesn't need or come with any drivers.

---

