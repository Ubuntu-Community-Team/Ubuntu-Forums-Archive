---
title: "X Resolution Issue"
date: 2012-03-28
forum: General Help
---

### Post by djc72uk on 2012-03-28
[FONT=Ubuntu][SIZE=2]Hi experts,[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]Relative newbie here.[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]I've search several threads here in order to remedy my problem particularly [http://ubuntuforums.org/showthread.php?t=1948071&highlight=xrandr](http://ubuntuforums.org/showthread.php?t=1948071&highlight=xrandr) however, none seem to fit my problem exactly.  This is my first Ubuntu thread so apologies if it's been created under the incorrect category or doesn't follow the usual format. [/SIZE][/FONT] 
 

 [FONT=Ubuntu][SIZE=2]So here goes :)
[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]Having recently installed Ubuntu 10.11 one of the first things I was displeased with was the resolution.  As per the thread above, I attempt to set a higher resolution using xrandr.  Here's the procedure I used to no avail: -[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]$ xrandr | grep max [/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]OK, my first assumption here is that 8192 x 8192 is possible:redface:?[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]$ cvt 8192 8192  60[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]# 8192x8192 60.00 Hz (CVT) hsync: 508.47 kHz; pclk: 5898.25 MHz [/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]Modeline "8192x8192_60.00"  5898.25  8192 8976 9896 11600  8192 8195 8205 8475 -hsync +vsync [/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]$ xrandr --newmode "8192x8192_60.00"  5898.25  8192 8976 9896 11600  8192 8195 8205 8475 -hsync +vsync[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]So far so good.  I guess?[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]Here's where it goes terribly wrong![/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]$ xrandr --addmode LVDS1 "8192x8192_60.00"[/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]X Error of failed request:  BadMatch (invalid parameter attributes) [/SIZE][/FONT]
   [FONT=Ubuntu][SIZE=2]Major opcode of failed request:  150 (RANDR) [/SIZE][/FONT]
   [FONT=Ubuntu][SIZE=2]Minor opcode of failed request:  18 (RRAddOutputMode) [/SIZE][/FONT]
   [FONT=Ubuntu][SIZE=2]Serial number of failed request:  31 [/SIZE][/FONT]
   [FONT=Ubuntu][SIZE=2]Current serial number in output stream:  32[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]Yuck!  What does that mean?[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]I'm assuming that it's complaining about LVDS1?  LVDS1 is  showing as connected in the xrandr -q output: -[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]$ xrandr -q [/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192 [/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm [/SIZE][/FONT]
    [FONT=Ubuntu][SIZE=2]1366x768       60.0*+ [/SIZE][/FONT]
    [FONT=Ubuntu][SIZE=2]1360x768       59.8     60.0   [/SIZE][/FONT]
    [FONT=Ubuntu][SIZE=2]1024x768       60.0   [/SIZE][/FONT]
    [FONT=Ubuntu][SIZE=2]800x600        60.3     56.2   [/SIZE][/FONT]
    [FONT=Ubuntu][SIZE=2]640x480        59.9   [/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]VGA1 disconnected (normal left inverted right x axis y axis) [/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]HDMI1 disconnected (normal left inverted right x axis y axis) [/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]DP1 disconnected (normal left inverted right x axis y axis) [/SIZE][/FONT]
 [FONT=Ubuntu][SIZE=2]DP2 disconnected (normal left inverted right x axis y axis) [/SIZE][/FONT]
   [FONT=Ubuntu][SIZE=2]8192x8192_60.00 (0xbf) 1603.3MHz [/SIZE][/FONT]
         [FONT=Ubuntu][SIZE=2]h: width  8192 start 8976 end 9896 total 11600 skew    0 clock  138.2KHz [/SIZE][/FONT]
         [FONT=Ubuntu][SIZE=2]v: height 8192 start 8195 end 8205 total 8475           clock   16.3Hz[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]I've been unable to complete the procedure i.e. xrandr –output due the above problem so there may yet be further challenges.[/SIZE][/FONT]
 

 [FONT=Ubuntu][SIZE=2]DJC.[/SIZE][/FONT]

---

### Post by TeoBigusGeekus on 2012-03-28
First things first; what's your graphics card?
```
lshw -C display
```

---

### Post by djc72uk on 2012-03-28
Hi,

Thanks for the reply.  Please see below the required output: -

$ sudo lshw -C display
[sudo] password for djc72uk: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d2400000-d24fffff

DJC.

---

