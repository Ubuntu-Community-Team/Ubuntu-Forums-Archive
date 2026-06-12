---
title: "Sometimes at boot up I get a blank screen!"
date: 2009-06-25
forum: General Help
---

### Post by oxf on 2009-06-25
Is there a log saved anywhere of boot ups and any associated errors encountered? The reason I'm asking is this.

This little problem on my desktop is happening only occasionally. Most of the time it boots up fine without problem. What happens is this: the PC boots up, after the GRUB there is a very quick scrolling of boot commands/status down the screen (maybe errors? but too quick to read) and after boot the display is blank. My only option then is crash the system, after which it boots up fine again. I would say this only happens about 1 in 15-20 boot attempts so its a little difficult to get a handle on.
 
At this point I have very little information to go on so I'm wondering if there's anything I can do or log or anything else to diagnose and start to see what might be happening? 
 
Could it be a video card issue. When I look in System>Administration>Hardware Drivers I see I have three Nvidia drivers to choose from, none of which are enabled at this point. Right now I'm using whatever was installed by default when I installed Jaunty a few days back. Should I try one of these and if so how do I decide? Or is this nothing to do with the problem?
 
The other thing I should point out is that on boot up I get the "MS Bios bug error 8254 timer unable to connect to IO APIC" I get this on every boot but was advised to ignore it as it doesn't seem to be affecting anything.
 
So any ideas on how to start diagnosing this issue?
Thanks
 
Jaunty 9.04
Acer Aspire L100
Video Card: Nvidia GEforce 6150 LE

---

### Post by jake16424 on 2009-06-25
> **oxf said:**
> Is there a log saved anywhere of boot ups and any associated errors encountered? The reason I'm asking is this.

This little problem on my desktop is happening only occasionally. Most of the time it boots up fine without problem. What happens is this: the PC boots up, after the GRUB there is a very quick scrolling of boot commands/status down the screen (maybe errors? but too quick to read) and after boot the display is blank. My only option then is crash the system, after which it boots up fine again. I would say this only happens about 1 in 15-20 boot attempts so its a little difficult to get a handle on.
 
At this point I have very little information to go on so I'm wondering if there's anything I can do or log or anything else to diagnose and start to see what might be happening? 
 
Could it be a video card issue. When I look in System>Administration>Hardware Drivers I see I have three Nvidia drivers to choose from, none of which are enabled at this point. Right now I'm using whatever was installed by default when I installed Jaunty a few days back. Should I try one of these and if so how do I decide? Or is this nothing to do with the problem?
 
The other thing I should point out is that on boot up I get the "MS Bios bug error 8254 timer unable to connect to IO APIC" I get this on every boot but was advised to ignore it as it doesn't seem to be affecting anything.
 
So any ideas on how to start diagnosing this issue?
Thanks
 
Jaunty 9.04
Acer Aspire L100
Video Card: Nvidia GEforce 6150 LE


install Nvidia 180 and all the sub driver\packets with it.

nvidia doesn't play well with ubuntu in my run in with it, but tht should do you well. 

im running MINT7 so it might work fine for me and be h3ll for you to run.

---

### Post by oxf on 2009-06-25
> **jake16424 said:**
> install Nvidia 180 and all the sub driver\packets with it.

nvidia doesn't play well with ubuntu in my run in with it, but tht should do you well. 

im running MINT7 so it might work fine for me and be h3ll for you to run.

OK, I can try that. I'm curious what drivers do I have installed by default then?

---

### Post by Megrimn on 2009-06-25
Well, by default, you can use the VESA driver.

```
sudo displayconfig -gtk
```

use that to edit your driver and screen resolution.  If you can't get the nVidia driver to work, VESA is a good default.  I'm using it on my dad's laptop until I can get an internet connection

---

### Post by oxf on 2009-06-26
> **Megrimn said:**
> Well, by default, you can use the VESA driver.

```
sudo displayconfig -gtk
```use that to edit your driver and screen resolution.  If you can't get the nVidia driver to work, VESA is a good default.  I'm using it on my dad's laptop until I can get an internet connection

OK do I need disable the  default  driver, i.e Vesa, before I enable the  Nvidia 180 in Sysyem>Admin>HardwareDrivers ?
 I'm assuming I do.

---

### Post by minhaaj on 2010-10-08
I have the exact same problem on ubuntu lucid with dell inspiron 6400. My hardware is ATI Radeon 1400. Its just once in a while but i am still curious what is that thats the problem ? In my case i have to restart the computer after that and there is like red patches in a horizontal line on top of the screen and rest of the screen is black.

---

