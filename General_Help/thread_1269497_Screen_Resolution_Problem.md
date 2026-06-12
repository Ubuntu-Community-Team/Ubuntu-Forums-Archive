---
title: "Screen Resolution Problem"
date: 2009-09-18
forum: General Help
---

### Post by DouglasL on 2009-09-18
Right. My screen has the "capacity" of displaying 1280x1024 - which is what I always use.

But when I started my computer today it had just changed itself to 1024x768.
And I can't change it back to 1280x1024.

From what I've understood there's two ways you're supposed to be able to do this. From "nVidia X Settings" or whatever and the normal "Screen" option in settings.
Neither of them work.
1280x1024 is just not there in the list of resolutions.

Please help :3

---

### Post by fogNL on 2009-09-18
Is your monitor an LCD monitor or a CRT?

---

### Post by DouglasL on 2009-09-18
It's an LCD.
However, for some reason the nVidia X server interface calls it a CRT.

---

### Post by hencq on 2009-09-19
I have exactly the same problem. When I started my computer today, the resolution was set to 1024x768. Since I didn't change anything, it seems something went wrong with an update. Any idea how to fix it?

---

### Post by dfrodrig on 2009-09-19
Hello everyone,

I am having a similar problem, on Ubunto Hardy with a nvidia card EN7300GT, and nvidia accelerated graphics -driver n. 180

After installing nvidia drivers, I tried to run Nvidia xServer, i properly configured everything for using the screen 1920x1080 resolution and it works like a charm.

I save the configuration to /etc/X11/xorg.conf, and thus everything seems like should work. 

However, everytime I login again, resolution fall back to 800x600. Running xrandr, all resolutions are available,
""
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1920 x 1080
default connected 800x600+0+0 0mm x 0mm
(...)
""

I need to run nvidia-settings again, set 1920x1080, and finally i can work. Need to do it everytime after login, which is utterly annoying.

The xconf.org section for monitor and display:
""
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP 2159"
    HorizSync       24.0 - 94.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1920x1080_60 +0+0; 1920x1080 +0+0;"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
""


I appreciate any help, it's really annoying... I'm usually a Windows user that uses putty for working remotely on linux servers, but decided to give it a go to a linux desktop as well.... it's unpraticable to be running nvidia-settings everytime i reboot/login again.


Thanks,
daniel

---

### Post by NoaHall on 2009-09-19
You are using "gksudo nvidia-settings" to run it?

---

