---
title: "EDID Plasma and Nvidia Resolution problem"
date: 2010-03-07
forum: General Help
---

### Post by kempy1000 on 2010-03-07
Hello,

I am trying to get my plasma tv to display a PAL (720×576) signal over VGA.

I am using an Nvidia FX5200 card and the 173 driver. nvidia-settings only allows me two resoultions and the highest is 640x480. 

I tried modifying xorg.conf to add 720×576 as the only resolution option and when rebooted the display was unchanged, as if the resolution had just been ignored.

So I thought this was simply a case of overriding the EDID so using the utility get-edid I was going to get an edid.dat file and try manually specifying it in xorg.conf.

But get-edid gives this output:

```

get-edid: get-edid version 2.0.0

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0x11100 "NVIDIA"

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
        Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged

```

What does this mean?
Is there anyway to manual spesify a resolution that wont be ignored?

Thank you
Chris

---

