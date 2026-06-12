---
title: "how to enable 800x600@60hz in xrandr"
date: 2009-09-27
forum: General Help
---

### Post by Jamesss on 2009-09-27
I have a nvidia GeForce2 MX/MX 400 graphics card with the nvidia proprietary driver (version 96) in ubuntu jaunty. I'm comfortably running 1280x1024 on my monitor, but whenever I plug in my projector I need to manually switch the resolution to 800 x 600 @ 60hz. I can do this via nvidia-settings but would like to automate it with a script. xrandr -q reports:

```
Screen 0: minimum 320 x 175, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0* 
   1024x768       51.0     57.0     58.0     59.0  
   1280x960       52.0  
   1152x864       53.0     54.0     55.0     56.0  
   960x540        60.0  
   840x525        61.0     62.0  
   832x624        63.0  
   800x600        64.0     65.0     66.0     67.0     68.0     69.0     70.0  
   800x512        71.0  
   720x450        72.0  
   720x400        73.0  
   680x384        74.0     75.0  
   640x512        76.0  
   640x480        77.0     78.0     79.0     80.0     81.0  
   640x400        82.0  
   640x350        83.0  
   576x432        84.0     85.0     86.0     87.0  
   512x384        88.0     89.0     90.0     91.0  
   416x312        92.0  
   400x300        93.0     94.0     95.0     96.0     97.0  
   360x200        98.0  
   320x240        99.0    100.0    101.0    102.0  
   320x200       103.0  
   320x175       104.0  

```

I added a new line with:
```
xrandr --newline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsyncD
```

and now xrandr reports:

```
Screen 0: minimum 320 x 175, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0* 
   1024x768       51.0     57.0     58.0     59.0  
   1280x960       52.0  
   1152x864       53.0     54.0     55.0     56.0  
   960x540        60.0  
   840x525        61.0     62.0  
   832x624        63.0  
   800x600        64.0     65.0     66.0     67.0     68.0     69.0     70.0  
   800x512        71.0  
   720x450        72.0  
   720x400        73.0  
   680x384        74.0     75.0  
   640x512        76.0  
   640x480        77.0     78.0     79.0     80.0     81.0  
   640x400        82.0  
   640x350        83.0  
   576x432        84.0     85.0     86.0     87.0  
   512x384        88.0     89.0     90.0     91.0  
   416x312        92.0  
   400x300        93.0     94.0     95.0     96.0     97.0  
   360x200        98.0  
   320x240        99.0    100.0    101.0    102.0  
   320x200       103.0  
   320x175       104.0  
  800x600_60.00 (0x121)   38.2MHz
        h: width   800 start  832 end  912 total 1024 skew    0 clock   37.3KHz
        v: height  600 start  601 end  604 total  622           clock   60.0Hz
```

However, I can't select this resolution, xrandr just reports:
```
james@james-desktop:~$ xrandr -s 24
Size index 24 is too large, there are only 24 sizes
```

can anyone help?

---

### Post by wojox on 2009-09-27
I think you need --newmode

```
xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsyncD 
```

---

### Post by Jamesss on 2009-09-28
ok I tried --newmode but there's no change.

any other ideas? Can I control nvidia-settings from the command line?

---

