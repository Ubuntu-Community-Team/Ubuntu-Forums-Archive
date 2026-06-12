---
title: "Can't set resolution to 1920x1080..."
date: 2012-07-23
forum: General Help
---

### Post by qwertz123 on 2012-07-23
Hi, I have some problems setting my screen resolution, maybe you can help me on this...

I am using ubuntu 11.10 64 bit with an intel graphic chip:
```
user@computer:~$ sudo lspci -v
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0420
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at f7c00000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at ecb8 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: i915
```My screen is a 23" Asus that supports HD resolution of 1920x1080. It works perfectly fine under WIndows 7, but the maximum resolution I can choose under ubuntu is 1440x900. When I installed ubuntu I used another monitor that was connected via the VGA port. 1440x900 might have been its native resolution...

I use the displayport and a DVI cable to connect the monitor. After reading up a bit, I did the following, but did not manage to set my resolution to 1920x1080:

```
user@computer:~$ sudo get-edid | parse-edid
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11100 "Intel(R)Eaglelake Graphics Chipset Accelerated VGA BIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination does not support DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

parse-edid: EDID checksum passed.

    # EDID version 1 revision 3
Section "Monitor"
    # Block type: 2:0 3:ff
    # Block type: 2:0 3:fd
    # Block type: 2:0 3:fc
    Identifier "ASUS VH238"
    VendorName "ACI"
    ModelName "ASUS VH238"
    # Block type: 2:0 3:ff
    # Block type: 2:0 3:fd
    HorizSync 30-85
    VertRefresh 55-75
    # Max dot clock (video bandwidth) 190 MHz
    # Block type: 2:0 3:fc
    # DPMS capabilities: Active off:yes  Suspend:no  Standby:no

    Mode     "1920x1080"    # vfreq 60.000Hz, hfreq 67.500kHz
        DotClock    148.500000
        HTimings    1920 2008 2052 2200
        VTimings    1080 1084 1089 1125
        Flags    "+HSync" "+VSync"
    EndMode
    # Block type: 2:0 3:ff
    # Block type: 2:0 3:fd
    # Block type: 2:0 3:fc
EndSection
```So it seems to read the right EDID. Next thing I did was trying to change the resolution via xrandr. There, as in the display settings, the maximum resolution was listed as 1440x900. 

```
user@computer:~$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

user@computer:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

user@computer:~$ xrandr --addmode DP1 1920x1080_60.00

user@computer:~$ xrandr --output DP1 -- mode 1920x1080_60.00
```That did not work, unfortunately. It switches back to 1440x900.

However, the new resolution is listed in the displey setting now. But when I try to apply it, I get a CRTC 63 error:
> 
The selected configuration for displays could not be applied
could not set the configuration for CRTC 63Does anyone has an idea what might be wrong? There should be an easy fix I guess. As everything works perfectly under windows. I have the feeling it is somehow stuck on that strange 1440x900 resolution because I installed ubuntu using a monitor with most likely that resolution...

Thanks!

---

### Post by papibe on 2012-07-23
Hi qwertz123.

You should form a modeline using the EDID info.

Take this:
> **qwertz123 said:**
> ```

    Mode     "1920x1080"    # vfreq 60.000Hz, hfreq 67.500kHz
        DotClock    148.500000
        HTimings    1920 2008 2052 2200
        VTimings    1080 1084 1089 1125
        Flags    "+HSync" "+VSync"
    EndMode
```

And use those same numbers.

```
# vfreq 60.000Hz, hfreq 67.500kHz
Modeline "1920x1080_60" 148.50  1920 2008 2052 2200  1080 1084 1089 1125  +HSync +VSync
```
Hope it helps, and let us know how it goes.
Regards.

---

### Post by qwertz123 on 2012-07-24
Thanks, but unfortunately it did not help. I get the same error... Any other idea?

---

### Post by rgd55 on 2012-07-29
Same problem here.

---

### Post by qwertz123 on 2012-10-07
I gave it another try, hoping some updates have changed something, but no luck :(

Does anyone have another idea on how to set my resolution to 1920x1080?

---

