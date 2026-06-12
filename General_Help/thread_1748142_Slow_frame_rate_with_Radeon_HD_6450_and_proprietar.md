---
title: "Slow frame rate with Radeon HD 6450 and proprietary drivers under Natty 11.04"
date: 2011-05-03
forum: General Help
---

### Post by blimbo on 2011-05-03
Hi gang,

I just upgraded to 11.04 from 10.10. I have a Radeon 6450 with 1GB of video RAM which should give me pretty good performance, but I'm only getting a measly 60 fps with the new ATI diver (11.4). I installed like this, making sure I'd removed the open source driver:

sh ati-driver-installer-11-4-x86.x86_64.run --buildpkg Ubuntu/natty

Then installed the debs and ran an aticonfig --initial. The module builds and installs fine:

tnugent@translocon:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6450
OpenGL version string: 4.1.10666 Compatibility Profile Context

But this is not good:

tnugent@translocon:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
274 frames in 5.0 seconds = 54.800 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS

Frame rate was much better under 10.10 with the proprietary driver (11.3) but that version doesn't build under Natty.

Anyone got any ideas?

Cheers,

Tim

p.s.

tnugent@translocon:~$ uname -a
Linux translocon 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
tnugent@translocon:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: NI Caicos [AMD RADEON HD 6450]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:54 memory:d0000000-dfffffff memory:e1420000-e143ffff ioport:3000(size=256) memory:e1400000-e141ffff

---

### Post by RobertVarga on 2011-05-03
I also have an Ati Radeon HD and because i wanted to keep the bootsplash resolution nice, i decided to not to install any drivers from ati, lets  go without. and it works. also desktop is beautiful. i just discovered ati drivers mass up the sys.

---

### Post by blimbo on 2011-05-03
I saw here that the Radeon HD 6450 needs a very recent version of mesa to get 3D acceleration with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

That requires compiling mesa from git which I'm not sure I want to do right now..

Happy Koninginnedag for last Saturday btw :-)

---

### Post by blimbo on 2011-05-04
Also, I have no desktop effects tab under system->preferences->appearance (using gnome desktop).. is this related or do they live somewhere else in Natty now (or did I remove a package I shouldn't have)?

---

### Post by rwsmith61 on 2011-05-04
> **blimbo said:**
> Also, I have no desktop effects tab under system->preferences->appearance (using gnome desktop).. is this related or do they live somewhere else in Natty now (or did I remove a package I shouldn't have)?

Glad you mentioned this. I thought it was just me and a messed up install. It might be related to the Unity movement (of which I am no fan).

Not sure about the frame rates for glxgears, but it appears that it now syncs with the framerate of your monitor. My monitor is 75Hz and glxgears reports 75fps. I have an ATI 4550 card, P8P67 i7-2600K, and 8GB DDR3-1600 RAM. Running Natty 11.04.

---

### Post by blimbo on 2011-05-04
I solved my frame rate issue. In 10.10 I had turned 'tear free' on and set 'wait for vertical refresh' to 'quality' (both these made things very nice) in Catalyst control centre. I guess the same settings for picked up on upgrade to 11.04. Anyway, I turned 'tear free' off and set vertical refresh' to 'performance' and my frame rate has jumped from about 60fps to 900fps so that's good. 

Apparently in Natty you must use CompizConfig settings manager to get effects when using gnome.

---

