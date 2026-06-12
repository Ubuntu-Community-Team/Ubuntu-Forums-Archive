---
title: "Nouveau support for two graphic cards"
date: 2011-09-27
forum: General Help
---

### Post by zamboni_luca on 2011-09-27
Hi guys,
I have installed the nouveau driver (compiled for 1.10.1, module version = 0.0.16) for my system which consists of two NVIDIA GPUs:
02:00.0 VGA compatible controller: nVidia Corporation G96 [Quadro FX 380] (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GF100 [Tesla C2050 / C2070] (rev a3)

The single screen is connected to the GPU on PCI 02:00.0. The xorg.conf file only contains:
Section "Device"
Identifier "n"
Driver "nouveau"
EndSection

My problem is that I want to be able to use the GPU on 03:00.0 but it seems there is something wrong that doesnt allow me to do that. In particular:
1) From lspci -vvv
03:00.0 VGA compatible controller: nVidia Corporation GF100 [Tesla C2050 / C2070] 
...
Kernel modules: nouveau, nvidiafb

while the other card shows nouveau driver being in use:
02:00.0 VGA compatible controller: nVidia Corporation G96 [Quadro FX 380]
...
Kernel driver in use: nouveau
Kernel modules: nouveau, nvidiafb

2) From dmesg there seems to be an error:
[    9.209694] nouveau 0000:03:00.0: enabling device (0000 -> 0003)
[    9.209702] nouveau 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.209709] nouveau 0000:03:00.0: setting latency timer to 64
[    9.210528] [drm] nouveau 0000:03:00.0: Detected an NVc0 generation card (0x0c0880a3)
[    9.219121] [drm] nouveau 0000:03:00.0: Failed to map PRAMIN BAR
[    9.219739] nouveau 0000:03:00.0: PCI INT A disabled
[    9.219744] nouveau: probe of 0000:03:00.0 failed with error -12

I tried to modify the xorg.conf file changing the device to use and specifying the BusID of the second card but when I do it, the system freezes at boot right after checking battery state.

Thanks in avance for your help

---

