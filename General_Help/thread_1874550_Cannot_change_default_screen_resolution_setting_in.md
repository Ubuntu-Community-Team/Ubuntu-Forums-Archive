---
title: "Cannot change default screen resolution setting in xrandr"
date: 2011-11-03
forum: General Help
---

### Post by A4Skyhawk on 2011-11-03
I have Nvidia GeForce 6150SE nForce 430, using Ubuntu 10.04  LTS.  I would like to increase the resoution of my monitor to 1280x1024x75.  After entering *suto nvidia-settings* I get the Nvidia  GUI.  When I select X Screen 0 in the GUI, the information that displays indicates  that the screen dimensions are 1152x864 pixels (325x228 millimeters),  which is the default setting indicated in Xrandr (see below) that resets on every bootup.  However, when  I select X Server Display Configuration in the GUI, the options for  layout/resolution show the option for 1280x1024x75, which is also shown  in the monitor's user manual.  If I select 1280x1024x75, the monitor  operates satisfactorily.  If I select 'Save to X Configuration File' in  the GUI, the default setting is changed in the xrandr file, but resets  to 1152x864 on the next bootup.
     Here is the response to *$ xrandr -q* after bootup:
Screen 0: minimum 320 x 175, current 1152 x 864, maximum 1280 x 1024
default connected 1152x864+0+0 0mm x 0mm
   1280x1024      50.0     51.0     52.0     53.0  
   1280x960       54.0     55.0  
   1152x864       56.0*    57.0     58.0     59.0     60.0     61.0  
   1024x768       62.0     63.0     64.0     65.0     66.0  
   960x600        67.0  
   960x540        68.0  
   928x696        69.0  
   896x672        70.0  
   840x525        71.0     72.0     73.0     74.0  
   832x624        75.0  
   800x600        76.0     77.0     78.0     79.0     80.0     81.0     82.0     83.0     84.0  
   800x512        85.0  
   720x450        86.0  
   720x400        87.0  
   680x384        88.0     89.0  
   640x512        90.0     91.0  
   640x480        92.0     93.0     94.0     95.0     96.0     97.0     98.0  
   640x400        99.0  
   640x350       100.0  
   576x432       101.0    102.0    103.0    104.0    105.0    106.0  
   512x384       107.0    108.0    109.0    110.0    111.0  
   416x312       112.0  
   400x300       113.0    114.0    115.0    116.0    117.0  
   360x200       118.0  
   320x240       119.0    120.0    121.0    122.0  
   320x200       123.0  
   320x175       124.0 
     In the last 2 days I have tried many suggestions from the forum w/ no success.  Hope someone can help.
TIA,
Bill

---

### Post by A4Skyhawk on 2011-11-04
Solved.  See post #23 of following thread, dated 8/17/2009 ----------------
[http://ubuntuforums.org/showthread.php?t=1242804&highlight=resolution+sticks%2C+desktop+effects]("http://ubuntuforums.org/showthread.php?t=1242804&highlight=resolution+sticks%2C+desktop+effects")

Bill

---

