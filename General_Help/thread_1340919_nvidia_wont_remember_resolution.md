---
title: "nvidia wont remember resolution"
date: 2009-11-29
forum: General Help
---

### Post by nexoncore on 2009-11-29
Could someone help with my problem.

I am using an nvidia geforce 7100 / nforce 6 graphics card built into the motherboard. I know ubuntu can work fine with it because it has before.

I am running the 185 driver, and everything seems to run fine but the resolution cant be saved. Every time I logout or restart it reverts to the 800x600 resolution.

Whats worse though, is the login screen is 1024x768 which is what I want, but when I login it reverts to 800x600

Bellow is my xorg.conf
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    VendorName     "NVIDIA Corporation
EndSection
```

---

### Post by sensay on 2009-11-29
Are you running nvidia-settings as root? I had a similar issue that my RES would always change to 1920 x 1440 when i wanted 1600 x 1200. Running sudo nvidia-settings from the terminal and saving the xorg.conf file after making changes worked for me.

Cheers

---

### Post by nexoncore on 2009-11-29
I found the problem. Gnome was changing resolution by itself,, overriding nvidia settings.

Changed display again but instead of using nvidia settings, used default gnome. Seems to have sorted itself.

---

### Post by atl_jimbo on 2009-12-26
I just had the same problem.  After a reboot the resolution would revert to 800X600 every time.  When going to System>Preferences>Display I would get the error message:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

I assumed it meant that clicking no would just end the process, not actually open the Display window and I always clicked yes and used the nvidia interface.  After many hours of editing /etc/X11/xorg.conf to try to correct this problem, I stumbled upon the solution.  At the prompt, click NO.  Change it to the resolution you want.  Fixed.

---

### Post by dcstar on 2009-12-27
> **atl_jimbo said:**
> I just had the same problem.  After a reboot the resolution would revert to 800X600 every time.  When going to System>Preferences>Display I would get the error message:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

I assumed it meant that clicking no would just end the process, not actually open the Display window and I always clicked yes and used the nvidia interface.  After many hours of editing /etc/X11/xorg.conf to try to correct this problem, I stumbled upon the solution.  At the prompt, click NO.  Change it to the resolution you want.  Fixed.

All these settings are (usually) in the .nvidia folder, simply delete it to reset everything back to standard.

---

