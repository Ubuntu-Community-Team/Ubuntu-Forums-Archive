---
title: "NVIDIA 8400GS: low graphics mode"
date: 2011-08-10
forum: General Help
---

### Post by stefangr1 on 2011-08-10
A few days ago, I upgraded my system from the EOL 9.04 to 10.04LTS. This did go relatively well, though the upgrade process reported some "could not update" errors for the NVIDIA drivers and at the first boot it reported it had to start in low graphics mode.

I noticed that I had manually installed drivers from NVIDIA's website before the upgrade, while afterwards the hardware drivers from the package manager had been enabled. I then disabled Ubuntu's drivers, and attempted to manually reinstall NVIDIA's own drivers. This resulted in some errors related to the install script not being able to find some vdpau related stuff. Something interesting then occured. As root everything worked flawless, but as normal user I still ended up with errors resulting Ubuntu to continue in low graphics mode. So I enabled the package managers driver again. This seemed to solve all  issues for the next 5 boots.

Until this morning, I again get a black screen with only a blinking "_" on the screen for quite some time, after which (nice feature) Ubuntu proposes to continue in low graphics mode. Here is a relevant part from my syslog:

Aug 10 08:17:53 linux kernel: [   24.075265] [TTM] Zone  kernel: Available graphics memory: 1028724 kiB.
Aug 10 08:17:53 linux kernel: [   24.075275] [drm] nouveau 0000:04:00.0: 256 MiB VRAM
Aug 10 08:17:53 linux kernel: [   24.097167] [drm] nouveau 0000:04:00.0: 512 MiB GART (aperture)
Aug 10 08:17:53 linux kernel: [   24.098283] [drm] nouveau 0000:04:00.0: Allocating FIFO number 1
Aug 10 08:17:53 linux kernel: [   24.102934] [drm] nouveau 0000:04:00.0: nouveau_channel_alloc: initialised FIFO 1
Aug 10 08:17:53 linux kernel: [   24.103515] [drm] nouveau 0000:04:00.0: Detected a DAC output
Aug 10 08:17:53 linux kernel: [   24.103518] [drm] nouveau 0000:04:00.0: Detected a TMDS output
Aug 10 08:17:53 linux kernel: [   24.103521] [drm] nouveau 0000:04:00.0: DCB encoder 1 unknown
Aug 10 08:17:53 linux kernel: [   24.103522] [drm] nouveau 0000:04:00.0: Detected a DAC output
Aug 10 08:17:53 linux kernel: [   24.103526] [drm] nouveau 0000:04:00.0: Detected a VGA connector
Aug 10 08:17:53 linux kernel: [   24.103577] [drm] nouveau 0000:04:00.0: Detected a DVI-I connector
Aug 10 08:17:53 linux kernel: [   24.858579] nvidia: module license 'NVIDIA' taints kernel.
Aug 10 08:17:53 linux kernel: [   24.858583] Disabling lock debugging due to kernel taint
Aug 10 08:17:54 linux kernel: [   25.401599] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
Aug 10 08:17:54 linux kernel: [   25.632700] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Aug 10 08:17:54 linux kernel: [   25.632704] NVRM: This can occur when a driver such as nouveau, rivafb,
Aug 10 08:17:54 linux kernel: [   25.632705] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Aug 10 08:17:54 linux kernel: [   25.632706] NVRM: the NVIDIA device(s).
Aug 10 08:17:54 linux kernel: [   25.632708] NVRM: Try unloading the conflicting kernel module (and/or
Aug 10 08:17:54 linux kernel: [   25.632709] NVRM: reconfigure your kernel without the conflicting
Aug 10 08:17:54 linux kernel: [   25.632710] NVRM: driver(s)), then try loading the NVIDIA kernel module
Aug 10 08:17:54 linux kernel: [   25.632711] NVRM: again.
Aug 10 08:17:54 linux kernel: [   25.632713] NVRM: No NVIDIA graphics adapter probed!

Any ideas on how to fix this?

---

### Post by stefangr1 on 2011-08-10
Any Ubuntu experts' tips? :D

---

### Post by sbraz on 2011-08-10
i'm a total n00b at nvidia drivers as i have ati cards (which btw is the bad side of vga drivers hell).

anyway i'd try to backup&remove your current xorg.conf,  purge everything related to nvidia graphic cards but modealiases, then reinstalling them using the hardware drivers utility under administration.

if it  works consistently under root but not while you are a normal user you might have some issues with file permissions.

this might help too [http://www.youtube.com/watch?v=2QsP8GDTpno](http://www.youtube.com/watch?v=2QsP8GDTpno)
the fun part begins at more or less half of the video

---

### Post by Frogs Hair on 2011-08-10
I use a 512 Mb version of that card .The Nvidia current driver from additional drivers has worked fine all four Ubuntu releases I have used .(clean installations)

The current Nvidia driver from the repository for 11.04 is 270.41.06 . Try what sbraz suggested .

---

