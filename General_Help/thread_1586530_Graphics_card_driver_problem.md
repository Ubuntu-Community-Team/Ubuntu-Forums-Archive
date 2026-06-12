---
title: "Graphics card driver problem"
date: 2010-10-02
forum: General Help
---

### Post by redbullcat on 2010-10-02
Hi, I'm new here, please don't shout at me :)

I've been using Ubuntu on and off for the last couple of years. Now I'm using Xubuntu 10.04 and want to have a real go at it.

My problem: I need to get the graphics  card driver installed for my ATI Graphics Card (an ATI Radeon x600). Problem is, nothing seems to work. My system is Xubuntu 10.04 64 bit, and I've downloaded the correct drivers from ATI's site, tried to run these (it brings up an error, more below). I've tried to turn these into .deb's with no luck, and I've tried the fglrx drivers from the software centre. All with absolutely no luck.

So can anyone help me? I've undid all I've done previously, so it's pretty much a clean slate.

Errors: when I try to run the .run's from ATI's site, I run it in terminal under [sudo sh]. It gives me this error:

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.32-25-generic; make sure that the version is being
correctly set by --iscurrentdistro

I've tried turning it into a .deb file with no luck, using a variety of methods.




So, please could somebody tell me the easiest way to get this installed? Thanks!

redbullcat

EDIT: sorry about the smilie in the error message, the text is [: x] (Without brackets and space).

---

### Post by sinamorawej on 2010-10-02
Hi

You are trying to install a 32bit package on a 64bit kernal. This is what the error is telling you.
Try to look for you driver in synaptic i.e. search for ATI.

---

### Post by redbullcat on 2010-10-02
OK, I will do!

Thanks a lot! Shows I'm still learning :D

---

### Post by redbullcat on 2010-10-02
Well, it seemed that didn't work. On Hardware Drivers in the System menu, it says [No proprietary drivers are in use on this system]. Does that mean anything?

---

### Post by gradinaruvasile on 2010-10-02
x600 is not supported anymore by the ati proprietary driver since version 9.3 that works only up to Ubuntu 8.10's x server.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

Short version - your card is not supported anymore by ati (only the HD2xxx or newer versions are supported).

You can either :
1. Downgrade to Ubuntu 8.10 (or lower versions) and install the 9.3 driver;
2. Use the current open source driver.

---

### Post by redbullcat on 2010-10-02
@gradinaruvasile

No way am I going back down to 8.10, I had enough trouble setting 10.04 up! :) :)

What is the current option source driver and where I can get?

:)

---

### Post by envygeeks on 2010-10-02
On a graphics card like that it's not worth it to install ATI, people mostly install proprietary drivers to get 3D acceleration.  With your graphics card you couldn't handle compiz very well anyhow so it's better to just stick with Vesa and configure vesa to support your monitors resolution, if not already supported without configuration.  You'll be quite fine with Vesa if you just remember what I said at first.

---

### Post by redbullcat on 2010-10-02
Thing is, I want (need :P) to play Minecraft. I can play on Windows just fine, but I'd love to play On Ubuntu as well. I d/led the minecraft.jar file, and logged in, and it shows a loading screen, then it goes black and doesn't do anything. My suspicion is I need the graphics  card drivers to play it, as I have Java and everything I need to do with Java. (I installed OpenJDK from the Software Centre).

---

### Post by gradinaruvasile on 2010-10-02
> **envygeeks said:**
> On a graphics card like that it's not worth it to install ATI, people mostly install proprietary drivers to get 3D acceleration.  With your graphics card you couldn't handle compiz very well anyhow so it's better to just stick with Vesa and configure vesa to support your monitors resolution, if not already supported without configuration.  You'll be quite fine with Vesa if you just remember what I said at first.

The driver for ati cards is not "vesa", it is the "radeon" open source driver (built on the specifications ATI/AMD released). The "vesa" driver has absolutely no 3d support (it is good only as a failsafe option for desktop users).
The "radeon" driver has 3d support, some 3d games work with it quite well.

The x server automatically uses this driver for ati cards if it has notimg specified in xorg.conf.

---

### Post by redbullcat on 2010-10-02
Well, I can't find the open source driver. Could anyone tell me the exact name of it in Synaptic? I REALLY need.want to play Minecraft :P

---

### Post by gradinaruvasile on 2010-10-02
> **gradinaruvasile said:**
> 

The x server automatically uses this driver for ati cards if it has nothing specified in xorg.conf.


This (fixed typo).


If you really need to see the driver, open a terminal and type: 

```
lsmod | grep radeon
```

PS: Most of the drivers (mainboard chipsets, audio, usb, sata, cpu, net cards, webcam, ) used by Linux are in the kernel and loaded automatically, no additional actions required.

Only the non-free drivers such as the proprietary nvidia, ati (fglrx), some wireless drivers or other exotic drivers are to be installed by compiling the kernel module.

---

### Post by Mark Phelps on 2010-10-02
The open-source driver is installed by default.  SO, unless you manually installed something yourself, you already HAVE the open-source drive in place.

---

