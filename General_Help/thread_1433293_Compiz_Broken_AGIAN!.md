---
title: "Compiz Broken AGIAN!"
date: 2010-03-18
forum: General Help
---

### Post by Plasma_NZ on 2010-03-18
Ok, no idea wtf is going on but getting entirely p'd at these things happening, if its not USB issues its compiz issues...

Have been using 

compiz --replace --only-current-screen 

for god knows how long, worked find no issues, now it doesnt do jack, and bitches about 

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option --only-current-screen

```

launching now with just compiz or compiz --replace - turns on compiz yet despite settings in compiz being set, they dont flaming work...

i've had about enough of these errors when nothings changed, i refuse to update to avoid these issues so - any ideas..

---

### Post by ManyuX95 on 2010-03-18
Try to reinstall it by going to synaptic

---

### Post by Plasma_NZ on 2010-03-18
Your logic is flawed.. nothings changed - so why would a reinstall make a difference..??

I mean i tried and as i figured nothing changes... still the same problem..

The problem is obviousyl with metacity - guessing they've removed a important function without relising others DO use it... 

It's a basic fix for compiz users who use dual-screen but only want compiz running on 1 of the screens...


like for myself for years, i've been running 2 monitors with 2 xsessions and only having compiz enabled on one....

---

### Post by Plasma_NZ on 2010-03-18
for now i'm reverting back to a previous kernel - works fine in that...

---

### Post by ManyuX95 on 2010-03-18
Sorry, Im used to Windows, and that is usually the solution to everything xD

---

### Post by becatron on 2010-03-18
Hi, I'm new here and I hope I posting in the right place, but I'm having issues getting compiz to work. I tried running compiz check and I got this:

 ```
Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3650
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```can anyone help me?

---

### Post by Ozymandias_117 on 2010-03-18
@becatron It's better if you make your own post. You're more likely to recieve help that way. According to the error message it looks like you need to install drivers for your graphics card. Try going to System -> Administration -> Hardware Drivers. If your gfx card is there, select it, and enable the driver.

---

### Post by Plasma_NZ on 2010-03-18
> **ManyuX95 said:**
> Sorry, Im used to Windows, and that is usually the solution to everything xD

well - time to forget all u know about windows cause it doesnt apply to linux ! :D

---

### Post by Plasma_NZ on 2010-03-18
> **becatron said:**
> Hi, I'm new here and I hope I posting in the right place, but I'm having issues getting compiz to work. I tried running compiz check and I got this:

 ```
Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3650
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```can anyone help me?

> **Ozymandias_117 said:**
> @becatron It's better if you make your own post. You're more likely to recieve help that way. According to the error message it looks like you need to install drivers for your graphics card. Try going to System -> Administration -> Hardware Drivers. If your gfx card is there, select it, and enable the driver.

I'd follow his advice on both parts... dont be scared to make your own threads... but as a guide for future reference - NVIDIA gfx cards are much simpler in linux than ati is..

---

### Post by 5735guy on 2010-03-20
Ubuntu purge compiz-fusion
[http://ubuntuforums.org/showthread.php?t=546429](http://ubuntuforums.org/showthread.php?t=546429)

Enabling Compiz Fusion On An Ubuntu 9.10 Desktop (NVIDIA Cards)
[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200)

ATI Cards

RadeonDriver
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

RadeonXpress
[https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress)

---

### Post by becatron on 2010-03-20
.. I don't think I have permission to start a new thread. My drivers seem fine, I doubled check and it's all installed fine. I removed and reinstalled just to be sure. Any other ideas?

---

