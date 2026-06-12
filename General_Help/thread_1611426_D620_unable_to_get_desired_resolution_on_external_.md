---
title: "D620 unable to get desired resolution on external monitor"
date: 2010-11-01
forum: General Help
---

### Post by bcmalloy on 2010-11-01
Hi I'm new to ubuntu 10.10 and I like it , currently running on a dell d620 on an external monitor (because the lcd has been removed) but am unfortunately unable to get a higher resolution than 1024X768.

When I type xrandr I get this output

--------------------------------------------------------------------------------------------------------------
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0 +
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1*    70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
mike@mike-Latitude-D620:~$

---------------------------------------------------------------------------------------------------------                                       
My monitor is on VGA1, I picked up the randr from another forum but have no idea how to change my resolution except through ther monitors icon under preferances, any help would be appeciated.

---

### Post by bcmalloy on 2010-11-02
Got it working it involved turning mirroring off in monitor options then locating the monitor app in the application directory as the desktop was spanned onto a no existent lcd so menu bar coud not be seen.

Then I was able to disable my  broken laptop lcd and run on the external screen only.
 
FANTASTIC This ubuntu 10.10 is bloody good, complete with par apps nzb leecher and everthing else I need, nice work.

---

