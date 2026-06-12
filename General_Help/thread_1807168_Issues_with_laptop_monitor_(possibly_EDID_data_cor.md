---
title: "Issues with laptop monitor (possibly EDID data corrupt?)"
date: 2011-07-18
forum: General Help
---

### Post by cgAtom on 2011-07-18
So after upgrading my 10.10 distro to natty i had a bunch of issues with the nvidia drivers and now ubuntu doesnt even detect my laptops monitor. Using the vesa driver i can at least use my screen but I definitely need 3D acceleration.

using read-edid I got this info:

[HTML]    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x2110 "NVIDIA"

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
parse-edid: IO error reading EDID[/HTML]

Any ideas on how i can fix this?

---

