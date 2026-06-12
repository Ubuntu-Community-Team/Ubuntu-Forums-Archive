---
title: "No 3D accel. in W7 VM with VirtualBox"
date: 2012-01-24
forum: General Help
---

### Post by rva1945 on 2012-01-24
Hi:

I'm running Ubuntu 10.10 as host, W7 as guest in a VirtualBox VM. In settings, the 3D acceleration is enabled, 64MB of display memory. But in W7, Dxdiag (DirectX diag tool) says Direct 3D acceleration, none. Just to play a game, one of the few reasons I keep a W7 at home.

(Terminal commands to see which is my card)
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

sudo lshw -C video
*-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5080(size=8)
 
Is there any issue with that?

Thanks

---

### Post by rva1945 on 2012-01-24
I learned that I need to install guest additions indicating 3D acceleration, but that must be made booting W7 in safe mode; ok, I did it, but now in safe mode, running Install guest additions, does nothing, no message, no nothing.

?

---

### Post by QIII on 2012-01-24
Misfire

---

### Post by QIII on 2012-01-24
If you mean that you ran "Install Guest Additions" from the actual VBox menu, that is normal.  You will have to shut down and restart your virtual machine.  When you restart, you will see what appears to be a CD.  On that will be a script/app to run in Windows.
I'm typing from my mobile right now so I can't post a link, but VirtualBox.org has a manual you can follow.

---

### Post by rva1945 on 2012-01-24
> **QIII said:**
> If you mean that you ran "Install Guest Additions" from the actual VBox menu, that is normal.  You will have to shut down and restart your virtual machine.  When you restart, you will see what appears to be a CD.  On that will be a script/app to run in Windows.
I'm typing from my mobile right now so I can't post a link, but VirtualBox.org has a manual you can follow.

Well, after trial-and-error sessions, I managed to run it. Now both DirectDraw acceleration and Direct3D acceleration are enabled. Now the game seems to launch but it enters in a loop of windows and I think now the problem is related to memory.

Thanks

---

### Post by xyzzyman on 2012-01-24
What game are you trying to run? The 3D acceleration is poised more for Aero and the like. Any game that really needs 3d acceleration is probably going to perform poorly. That's why I dual boot even though I use VM's the rest of the time.

---

### Post by rva1945 on 2012-01-24
> **xyzzyman said:**
> What game are you trying to run? The 3D acceleration is poised more for Aero and the like. Any game that really needs 3d acceleration is probably going to perform poorly. That's why I dual boot even though I use VM's the rest of the time.

KumaWar, and I fixed the issue. Now it works.

My problem now, unrelated to the topic, is that I can't control the game as there is no mouse neutral zone; it can't be set in W7 and i didn't find how to do it in Ubuntu (thinking that the settings in the host system affect the settings in the guest).

thanks

---

