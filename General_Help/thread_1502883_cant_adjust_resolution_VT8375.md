---
title: "cant adjust resolution VT8375"
date: 2010-06-06
forum: General Help
---

### Post by flyfox1 on 2010-06-06
I've followed the wiki but thats not working. First time xubuntu user.The font is so small its hurting my eyes. 
> 
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      60.0*    75.0  
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     60.0     56.0     65.0  
   640x480        75.0     73.0     67.0     60.0  
  800x600_60.00 (0x8a)   38.0MHz
        h: width   800 start  832 end  912 total 1024 skew    0 clock   37.1KHz
        v: height  600 start  603 end  607 total  624           clock   59.5HzMy graphics card is:
> 01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]I believe I'm using the openchrome driver. I would appreciate the help.

---

### Post by flyfox1 on 2010-06-06
fiixed sortta 


I changed this from the wiki
xrandr --output LVDS --mode 1024x768to this

xrandr --output default --mode 1024x768C

---

