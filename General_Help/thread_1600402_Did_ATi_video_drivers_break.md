---
title: "Did ATi video drivers break?"
date: 2010-10-18
forum: General Help
---

### Post by yodermk on 2010-10-18
Updated from Lucid to Maverick a week ago. Things were fine, and my integrated Radeon 3200HD seemed faster than under Lucid.

The system had been up all week, and suddenly some popups and some tooltips were all black, some windows had huge borders, and when I clicked on some menus they showed up as translucent grey with no text.  Desktop effects were otherwise still OK (I'm using KDE).

Rebooted. Desktop effects were so slow that they had to be disabled, plus some of the other problems still existed.

Left computer off for 8 hours, tried again, same thing.

Disabling desktop effects makes the computer usable.  I was just playing with Google Earth and it seems OK.

Any idea what's up?  I'm wondering if there's a hardware issue ...

---

### Post by yodermk on 2010-10-19
*bump* any quick thoughts here?  Happen to anyone else?  Just wondering if an update screwed something up (I think glibc was updated) or if it might be a hardware problem.

I'll try a live CD at some point to see if that works with effects. Haven't had a chance yet.

Found this in dmesg, not sure if it's related:

[   14.485014] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   14.676602] [drm] radeon defaulting to kernel modesetting.
[   14.676606] [drm] radeon kernel modesetting enabled.
[   14.676727] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.676732] radeon 0000:01:05.0: setting latency timer to 64

---

### Post by yodermk on 2010-10-24
Just tried a live CD.  That worked fine so no hardware problems.  Something in my install got screwed, and I don't think I did anothing other than normal updates.  Surely it happened to someone else?

My xorg.conf:
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
#       Option          "AccelMethod"   "exa"
#       Option          "DRI"           "on"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

---

### Post by wpshooter on 2010-12-27
> **yodermk said:**
> Just tried a live CD.  That worked fine so no hardware problems.  Something in my install got screwed, and I don't think I did anothing other than normal updates.  Surely it happened to someone else?

My xorg.conf:
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
#       Option          "AccelMethod"   "exa"
#       Option          "DRI"           "on"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

Yodermk:

Did you ever find the cause of your video problems ?

I am having random video problems with my ATI Radeon 9600 XT and I was wondering if this is a problem with the software that is included in Maverick ?

See my recent thread under the VIDEO section.

Thanks.

---

