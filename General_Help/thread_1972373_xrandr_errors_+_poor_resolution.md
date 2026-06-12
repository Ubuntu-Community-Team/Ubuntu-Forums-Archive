---
title: "xrandr errors + poor resolution"
date: 2012-05-03
forum: General Help
---

### Post by Chazara on 2012-05-03
Theres a few threads on the net with this problem but none of which help/directly relate to me.

heres whats what;
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  

```I created a modeline for the size I require for my monitor (1280x1024);
```

chazara@Chaz2P0:~$ cvt -v 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```then proceeded to use xrandr to create a newmode;
```

chazara@Chaz2P0:~$ xrandr --newmode "1280x1024_60Hz" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
xrandr: Failed to get size of gamma for output default

```It says "Failed to get size of gamma for output default" which it also did at "xrandr", but still displays the new mode;
```

chazara@Chaz2P0:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
  1280x1024_60Hz (0x178)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

```Addmode, regardless, refuses to accept;
```

chazara@Chaz2P0:~$ xrandr --addmode VGA1 "1280x1024_60Hz"
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "VGA1"

```Now, I'm not sure if I'm just being an idiot or not, but, I'm pretty sure the output can /only/ be VGA1... stuck a little bit here...

I also looked into creating a xorg.conf file in /etc/X11/ but seemed to just screw up my startup by doing so. 

The file looked (somewhat) like this;
```

Section "Screen" 
Identifier      "Default Screen"         
Device        "Monitor"         
Monitor       "LGMoniTor" 
DefaultDepth  24         
SubSection 
"Display"                 
Depth          24                 
Modes         "1280x1024"  "1024x768"   "640x480"         
EndSubSection 
EndSection

```Right now, I just really need someone to point me in the right direction. I'm pretty sure it can be solved in one of two ways;
A) Getting --addmode & --output to work
B) A better xorg.conf file

Much appreciated
Chazara

---

### Post by Chazara on 2012-05-03
AFK for a few hours. Need to feed myself + housemates

---

### Post by Chazara on 2012-05-04
Bump, problem persists. Any help would be appreciated :)

---

### Post by papibe on 2012-05-04
Hi Chazara.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the link here.

Regards.

---

### Post by Chazara on 2012-05-05
Hi there Papibe, thanks for the response.

Unfortunately I am currently staying at my mothers with having got some work in the area and will be away from my desktop for at least a week...

I will perform the var log as and when I can and shall be in touch. I hope you don't mind coming back to this in a few weeks time :)

Chaz

---

