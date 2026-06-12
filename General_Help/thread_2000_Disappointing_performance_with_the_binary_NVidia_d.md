---
title: "Disappointing performance with the binary NVidia driver"
date: 2004-10-24
forum: General Help
---

### Post by stodge on 2004-10-24
I installed the NVidia binary driver as per the instructions, and the results are very disappointing. In normal 2D desktop usage, the NVidia driver is slower than the nv driver. In 3D, the Torque demo ([http://www.garagegames.com](http://www.garagegames.com)) run at least 50% slower than under Windows. This was using a very un-scientific test of comparing FPS values at 800x600x32 in a window using OpenGL. I need to ensure that the NVidia GLX driver is being used instead of the Mesa software driver. Still the results in 2D and 3D are very disappointing compared with Windows.

---

### Post by stodge on 2004-10-24
I suppose this might explain why! Oops!

mike@dobber:~ $ cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.
mike@dobber:~ $ dmesg | grep AGP
agpgart: AGP aperture is 128M @ 0xd0000000
NVRM: not using NVAGP, AGPGART is loaded!!
NVRM: not using NVAGP, AGPGART is loaded!!

---

### Post by Julius on 2004-10-25
This is what mine says

Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

And I have followed the instructions that are described here:
[http://wiki.ubuntulinux.org/BinaryDriverHowto](http://wiki.ubuntulinux.org/BinaryDriverHowto)

---

### Post by stodge on 2004-10-25
I was trying out the other AGPART options. If I use this in my XF86Config file I get AGP enabled, but it's still slow.

Section "Device"
        Identifier      "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel" "1"
        Option          "AGPMode" "2x"
EndSection

And I know it's an old GeForce 2 GTS, but it's much slower than under Windows.

---

