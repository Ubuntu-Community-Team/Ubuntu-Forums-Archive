---
title: "k10temp riddle"
date: 2012-03-08
forum: General Help
---

### Post by QIII on 2012-03-08
k10temp - riddle me this

Got a crappy (but cheap!) ASRock A770DE+ motherboard to replace a long-suffering MSI board in my 24x7x365 rosetta@home machine.  Alas, the MSI gave up the ghost.

So, I put my machine back together with this board.  On it I stick the old Phenom II x4 920 (AM2+) and the old 8GB of DDR2 RAM (Yes, I wanted to reuse everything.)  There's also an ATI HD 4350 on it to fool the motherboard (which has no on board video) into thinking that I really give a crap -- but I run it headless anyway.

I decided to reinstall Oneiric just because.

So when I ran sensors-detect,  I got all the expected info -- except for k10temp.

Hmmm.  lsmod shows it.

Just for grins, I add k10temp manually to /etc/modules.  After reboot, still nothing.

But if if do 

```
sudo rmmod k10temp && sudo modprobe k10temp force=1
```I get

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)

```Well, I guess that's sort of getting somewhere. But I know my CPU shouldn't be freezing water at sea level.  And that doesn't persist through the next reboot and running sensors again finds k10temp AWOL again.

So:

lsmod -- check
/etc/modules -- check
sudo rmmod k10temp && sudo modprobe k10temp force=1  ... well, kinda.

No joy.

Anyone have any ideas besides re-rolling the module from source?  That would be plain aggravating on a clean install.

Edit:  It just occured to me that I could add the force=1 parameter on startup to see what happens

---

### Post by QIII on 2012-03-08
OK.  Adding the force=1 parameter on startup keeps me from having to start the module from the console.

But the sensor is still returning 0 degrees.

```
radeon-pci-0200
Adapter: PCI adapter
temp1:        +36.5°C  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)

w83627dhg-isa-0290
Adapter: ISA adapter
foo
bar
...

```

For the time being I'll just watch the socket temp and figure the CPU is hotter than that.  The temperature reading from k10temp is really just that odd "relative value for reference and not the actual physical temperature" thing AMD does anyway.

More later.

---

