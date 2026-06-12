---
title: "xrandr monitor rotating"
date: 2011-05-27
forum: General Help
---

### Post by tubalcainpc on 2011-05-27
Hi there, i've just bought a second monitor for my pc wich happens to be a pivot monitor. I already read lot of forums about my problem but somehow i dont find the solution, i have the same symptoms of dozens of existent thread but no matter whatever i try it just dont work.

i already changed the xorg.conf file and added at the device section just under Driver "nvidia" the following Otion"RandRRotation" "on" for my 2nd monitor

when i save and reboot i try to rotate my screen with

the nvidia settings going to  System > Preferences > Screen Resolution and choose either “left” or “right” for the rotation. It inmediately exits the nvidia settings and does nothing.

I tried with the terminal by typing

xrandr -o right and i get the following error

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

I actually managed to rotate it with Option "Rotate" "CCW", but the quality is really bad, as i can't change the size of the windows of the pdfs i try to read.


sudo lshw -c video
hiram@hiram-linux:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f8000000-f9ffffff memory:d8000000-dfffffff memory:d4000000-d7ffffff ioport:dc00(size=128) memory:fbd80000-fbdfffff

i would apreciate any help as i bought that monitor for the solely purpose of reading pdfs to write my thesis.

---

