---
title: "No display on screen after upgrading Nvidia Drivers"
date: 2010-09-26
forum: General Help
---

### Post by reffu on 2010-09-26
Recently I upgrade to the latest Nvidia driver for Linux. I checked that it was compatible with my Ubuntu 10.04 x64 system and my geforce gt 220 graphics card. I decided to go with the newest beta ver 260.1904. Installation went well, better actually than other times I tried to install the newest driver from their site. After installation was finished I restarted and let my system load up. As soon as it got past the ubuntu logo, the screen just went blank as if there was no signal. I determined that everything but the display was working. When I pressed ctrl-alt-F1 the numlock light turned off (this usually happens) and was still toggle-able. When I went through the other x-servers (ctrl-alt-(F2-F6)) the light went out but could be turned off and on by hitting numlock. When booting in from recovery mode, the screen displayed up to the point where it would show recovery options with no noticeable error showing before the screen turned off. This is what worries me the most.

I don't think it is my Xorg.conf because I replaced with a backup and still have the same problem.

Does anyone have any ideas about why this is happening or how I can at least see the terminal. 

As a side note, its definitely not the card because the card worked fine before, works in windows and live cds, and I tried with an older nvidia card and had the same problem.

---

### Post by tekkidd on 2010-09-26
I would suggest downgrade the nvidia drivers. First pop in the ubuntu live cd and navigate to 
```
/etc/X11/xorg.conf
```
make sure you do this on the HDD not the disk. Then look for block of text: 
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
```
then replace the "nvidia" with an "nv"
reboot

then reinstall the old drivers.

---

### Post by Mi11z on 2010-09-26
> **reffu said:**
> Recently I upgrade to the latest Nvidia driver for Linux. I checked that it was compatible with my Ubuntu 10.04 x64 system and my geforce gt 220 graphics card. I decided to go with the newest beta ver 260.1904. Installation went well, better actually than other times I tried to install the newest driver from their site. After installation was finished I restarted and let my system load up. As soon as it got past the ubuntu logo, the screen just went blank as if there was no signal. I determined that everything but the display was working. When I pressed ctrl-alt-F1 the numlock light turned off (this usually happens) and was still toggle-able. When I went through the other x-servers (ctrl-alt-(F2-F6)) the light went out but could be turned off and on by hitting numlock. When booting in from recovery mode, the screen displayed up to the point where it would show recovery options with no noticeable error showing before the screen turned off. This is what worries me the most.

I don't think it is my Xorg.conf because I replaced with a backup and still have the same problem.

Does anyone have any ideas about why this is happening or how I can at least see the terminal. 

As a side note, its definitely not the card because the card worked fine before, works in windows and live cds, and I tried with an older nvidia card and had the same problem.

Silly question but did you enable them afterwards?

---

### Post by reffu on 2010-09-26
I think I didn't because there was something about enabling it automatically during the install process. I might have misunderstood that part of the install. What do I have to do to make sure they are enabled? Would it cause a problem if I tried to enable them when they were already enabled? How can I check they are enabled? I'm not an ubuntu/linux noob but I've only ever done nvidia drivers once before.

Edit: Don't know if this helps but I just found this in my /var/log/Xorg.0.log 

(**) Sep 26 22:06:21 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 26 22:06:21 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 26 22:06:21 NVIDIA(0):     enabled.
(EE) Sep 26 22:06:21 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

---

