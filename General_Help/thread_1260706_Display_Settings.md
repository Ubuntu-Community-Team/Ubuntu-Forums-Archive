---
title: "Display Settings"
date: 2009-09-07
forum: General Help
---

### Post by starbright on 2009-09-07
Hello,

I recently connected my computer to a new screen and then the desktop resolution was too small so I changed it. But it would never stay when I would reboot the computer. It had worked fine with the other screen. Then all of the sudden after rebooting my computer, the resolution was set on 800x600, but when I try to change it, I can't. The only options are 800x600 or 640x480. I don't have any other options, although I had them all before. How can I change it again to the resolution that I want and make it stay?

---

### Post by redmk2 on 2009-09-08
> **starbright said:**
> Hello,

I recently connected my computer to a new screen and then the desktop resolution was too small so I changed it. But it would never stay when I would reboot the computer. It had worked fine with the other screen. Then all of the sudden after rebooting my computer, the resolution was set on 800x600, but when I try to change it, I can't. The only options are 800x600 or 640x480. I don't have any other options, although I had them all before. How can I change it again to the resolution that I want and make it stay?

I'm certainly no expert on this, but it appears that the new screen has not been identified by the the X-server.  On later versions of Ubuntu this is supposed to be automagically handled.

The file that actually controls the parameters is **/etc/X11/xorg.conf**.  I believe that if that file is missing it will be reconstructed. You can rename the file e.g. **xorg.conf.original** and see what you get.

In any event you can add the *modes* you need.  Here is the section for the screen for my system:```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc 3D Rage Pro AGP 1X/2X"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1600x1200" "1440x900" "1400x1050" "1280x1024" "
        EndSubSection
EndSection

```

As you can see I am using an ancient video card.  The monitor is a Samsung 19" wide screen (1440x900).  I had to add the modes to make it work.

---

### Post by starbright on 2009-09-09
Thanks! Now I have all of the resolutions available, but the resolution still will not stay after a reboot or if I log off. I still have to change my resolution every time. Any ideas on how to fix that?

---

