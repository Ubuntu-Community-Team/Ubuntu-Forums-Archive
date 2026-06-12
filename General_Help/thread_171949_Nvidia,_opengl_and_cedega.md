---
title: "Nvidia, opengl and cedega"
date: 2006-05-07
forum: General Help
---

### Post by Davidosky on 2006-05-07
Hi all,
i have installed Kubuntu Dapper for amd 64 bit (kernel 2.6.16-21). Today i have installed Cedega but i can't pass opengl test.

glxinfo |grep direct: > direct rendering: Yes

xorg.conf: > Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:3:0:0"
        VideoRam        262144
EndSection

What can i do?

---

### Post by mentar on 2007-04-15
Having the same problem, just the OpenGL test failing even though glxinfo reports that direct rendering is present
Uname -a output:
Linux mentar-laptop 2.6.17-11-generic #2 SMP Thu Feb 1 18:03:05 UTC 2007 x86_64 GNU/Linux

Got an NVidia GeForce Go 7200, it doesn't seem to be fully supported by Nvidia so maybe that's the problem in my case. Would be nice to get it to work though, so if anyone can figure this out there will be at least 2 happy people thanking you :D

---

### Post by banasw01 on 2007-07-20
Have exactly the same problem. Cedega says that I might be missing some 32bit emulation drivers on my 64bit system...

---

