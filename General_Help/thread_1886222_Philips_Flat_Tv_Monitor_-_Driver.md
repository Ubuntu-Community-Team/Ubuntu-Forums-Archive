---
title: "Philips Flat Tv Monitor - Driver?"
date: 2011-11-24
forum: General Help
---

### Post by JamesKenny on 2011-11-24
I am still fairly new to linux, I have only been using the os for the  past couple of months. I have a 32" inch philips flat tv that I am using  for a monitor. Before I bought it I read that it was limited to 1024px  and I was ok with the that. The problem is about a month ago the display  driver updated and when I went into settings > display it actually  called the monitor by name and let me adjust the screen to 1200 or 1600  pixels(i forget). Which was really nice. 

About two weeks ago I  lost the driver for my display again. (when i go into settings >  display its marked as unknown) and I am limited to 1024px again, which  again isn't really that bad (ctrl +/-), but having the option for a  better resolution makes me wish I had it back.

Any Suggestions?

ubuntu 11.x

james@dev:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  


*-core
       description: Motherboard
       product: 09E8h
       vendor: Hewlett-Packard
       physical id: 0
       serial: MXL6017XH
  
   *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786C2 v01.01
          date: 11/18/2004
          size: 128KiB
          capacity: 448KiB
           capabilities: pci pnp upgrade shadowing cdboot bootselect edd  int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720  int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot  zipboot biosbootspecification netboot
   
  *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: XU1 PROCESSOR
          size: 3200MHz
          width: 32 bits
          clock: 800MHz
           capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8  apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss  ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0

*-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfd00000-cfd7ffff ioport:1800(size=8) memory:e0000000-efffffff memory:cfd80000-cfdbffff

---

### Post by grahammechanical on 2011-11-24
You should always run a monitor or TV screen being used as a monitor at the optimum resolution set by the manufacturer. Forcing the monitor to run at a higher resolution could (would? Who knows?) damage it.

Do not say you were not warned and do not blame Ubuntu for breaking your monitor if you succeed in what you are trying to do.

My DTV/monitor has, according to the manufacturer Samsung, an optimum resolution of 1680 x 1050 @ 60 Hz and a maximum resolution of 1680 x 1050 @ 60 Hz. They are the same but maybe your TV has an optimum resolution and a higher maximum resolution. Even so it would be safer to stay at the optimum resolution that the display driver has detected.

Regards.

---

### Post by JamesKenny on 2011-11-24
Right now there isn't a driver for the monitor, but thats the part I don't understand is that there was a driver, and the driver recognized my tv, the driver has since disappeared.** I am not trying to force anything** I just wanted to know if maybe I could have done something to make the driver go away (like delete a software or change a download place), or where to look to replace the one I had already that recognized the monitor and could set it accordingly

---

