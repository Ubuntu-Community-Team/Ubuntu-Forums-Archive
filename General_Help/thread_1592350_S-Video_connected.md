---
title: "S-Video connected"
date: 2010-10-10
forum: General Help
---

### Post by Darac on 2010-10-10
I have this problem since i installed 10.10 today.

In my Preferences-> Monitors there's a "Unknown" monitor with max. resolution of 800x600. Now the problem is, my plymouth splash doesn't work and background of the login screen is 4 tiled backgrounds of 800x600. I ran xrandr and this is what i get:

```
:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
S-video connected (normal left inverted right x axis y axis)
   800x600        59.9 +
   640x480        59.9 
``` 

And here's my monitor.xml:
```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="VGA-0">
      </output>
      <output name="DVI-0">
          <vendor>SAM</vendor>
          <product>0x0218</product>
          <serial>0x4d453139</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="S-video">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>800</width>
          <height>600</height>
          <rate>60</rate>
          <x>1280</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
</monitors>
```
Strange thing is, i have nothing connected to S-video port, so i would like to disable it permanently since i will never use it on this comp. And i'm pretty sure it's the thing that's causing problems with plymouth and login screen.

One more thing that can help with the diagnostic, when i boot live 10.10 my screen resolution is also 800x600 and there's also an unknown monitor in Preferences->Monitor. Usually it was my samsung and an S-video there and it would boot into 1280x1024.

Any advices how to fix that "Unknown" so ubuntu knows recognizes it as S-Video or how to disable the S-video permanently? Switching that monitor to "off" doesn't solve the problem.

---

