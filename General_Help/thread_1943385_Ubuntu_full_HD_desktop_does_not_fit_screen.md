---
title: "Ubuntu full HD desktop does not fit screen"
date: 2012-03-19
forum: General Help
---

### Post by McDouglas on 2012-03-19
Hy i try to get workin a 42" amg42opsp04t1 ([[FONT=Arial][SIZE=2][COLOR=#000000][FONT=Arial]**[COLOR=#265b8d][FONT=Arial][B][FONT=Arial][FONT=Arial]AMG-42OPSP04T1-V1[/FONT][/FONT]**[/FONT][/COLOR][/B][/FONT][/COLOR][/SIZE][/FONT]]("http://www.amongo.com.cn/_d270058178.htm")) display with 1920x1080 pixel resolution. I'am currently using ubuntu 10.10 (touch driver supports only this).
As long I could not get any information about this even google cant help me (using ati driver fglrx AMD E350M1) 
The error is that the screen has 2 black gap on each side. 
looks like this:
llllll                  ---------- llllll
llllll    - screen     -llllll
llllll    - content    llllll
llllll                  ---------- llllll

Screen content is pushed.

Any help would be great.

On screen resolution 1600x900 everything is ok (desktop fits to the monitor correctly).
I work with VGA. Xorg.0.log displays no error. 
Interesting is that, the Monitor preferences shows 'sceptre tech inc 27" ' insted of the 42".


user@localhost:/$ xrandr -q
Screen 0: minimum 320 x 200, current 1080 x 1920, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1080x1920+0+0 left (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080      60.0* 
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       60.0     75.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   1024x600       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   800x480        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9  
   1080           60.0  




xorg.conf:
Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:0:1:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection




For someones, who have a same problem some keyword:
full hd, 1920x1080, amongo display, industrial monitor, desktop error, desktop size, screen size, 1600x900

---

