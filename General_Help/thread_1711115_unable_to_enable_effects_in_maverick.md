---
title: "unable to enable effects in maverick"
date: 2011-03-20
forum: General Help
---

### Post by maddbaron on 2011-03-20
Everything seems up to date but whenever I try to enable effects my system refuses, says the driver is missing. I check my drivers and they are all working properly. 
I'm confused by this.
Can anyone help me fix this please?

Thanks in Advance

---

### Post by bleedingsamurai on 2011-03-20
You might have a graphics card that isn't fully supported by the open drivers that come default. So to get all the accelerated spinners and whistles you will probably have to install the proprietary, "non-free" drivers. 
you should check out this link if you are using Ubuntu:
[http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/](http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/)
if you are using Kubuntu go to System and then Additional Drivers

then just install the graphics drivers, it will take some time because it is acutally rebuilding your kernel behind the GUI, and once it is done you will need to reboot to take advantage of the new drivers.

---

### Post by maddbaron on 2011-03-21
> **bleedingsamurai said:**
> You might have a graphics card that isn't fully supported by the open drivers that come default. So to get all the accelerated spinners and whistles you will probably have to install the proprietary, "non-free" drivers. 
you should check out this link if you are using Ubuntu:
[http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/](http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/)
if you are using Kubuntu go to System and then Additional Drivers

then just install the graphics drivers, it will take some time because it is acutally rebuilding your kernel behind the GUI, and once it is done you will need to reboot to take advantage of the new drivers.

But my drivers were working fine with ubuntu 10.04 before I upgraded to 10.10... thats y I'm confused. Is 10.10's driver system that much different?

---

### Post by Script Warlock on 2011-03-21
you forgot to mention your specs...

---

### Post by maddbaron on 2011-03-21
35-> **Script Warlock said:**
> you forgot to mention your specs...

AMD Athlon II Dual Core M320

Gnome 2.32.0 / Ubuntu 10.10 Maverick

Linux 2.6.35-28 Kernel

ATI Fire GL Driver

```
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 3949
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at f2300000 (32-bit, non-prefetchable) [size=64K]
	Memory at f2200000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

```

---

### Post by Script Warlock on 2011-03-21
what does it say 

fglrxinfo

---

### Post by maddbaron on 2011-03-21
> **Script Warlock said:**
> what does it say 

fglrxinfo

```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10362 Compatibility Profile Context

```

---

### Post by 5149.5 on 2011-03-21
After struggling with this off and on for few days, I finally resolved it on my system. I used Ubuntu Tweak to update my X11 files and the visual effects are running now.

---

### Post by maddbaron on 2011-03-21
> **5149.5 said:**
> After struggling with this off and on for few days, I finally resolved it on my system. I used Ubuntu Tweak to update my X11 files and the visual effects are running now.

how did u use tweak?

---

### Post by 5149.5 on 2011-03-21
> **maddbaron said:**
> how did u use tweak?


Source center > desktop > check the last two items in  the list > press refresh.

---

### Post by maddbaron on 2011-03-21
> **5149.5 said:**
> Source center > desktop > check the last two items in  the list > press refresh.

xorg-edgers fresh X crack? i had one checked but this unchecked, refreshed and I got a ton of xorg  updates along with a kernel update... this what u got after refresh?

---

### Post by 5149.5 on 2011-03-21
> **maddbaron said:**
> xorg-edgers fresh X crack? i had one checked but this unchecked, refreshed and I got a ton of xorg  updates along with a kernel update... this what u got after refresh?

Yeah. I got the same thing. I was a little hesitant when I saw the amount of changes to be made but all went well for me.

---

### Post by maddbaron on 2011-03-21
> **5149.5 said:**
> Yeah. I got the same thing. I was a little hesitant when I saw the amount of changes to be made but all went well for me.

i'll give it a go and hope it works....

---

### Post by maddbaron on 2011-03-21
this is so weird... the xorg update removed the desktop glitches i was having but my webcam doesn't work(wasn't working all that great before now it's really not working) and i hear a ringing sound when I try to start it.  and I still can't enable desktop effects...it gives a try like it wants to enable but then it goes back to what it was.... something is wrong with my xorg and i don't know what it is.

help anyone please?

---

### Post by maddbaron on 2011-03-24
bump

---

