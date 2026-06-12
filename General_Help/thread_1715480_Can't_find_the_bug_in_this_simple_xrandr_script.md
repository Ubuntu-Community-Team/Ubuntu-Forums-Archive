---
title: "Can't find the bug in this simple xrandr script?"
date: 2011-03-27
forum: General Help
---

### Post by hydrox24 on 2011-03-27
Hi guys, I have Ubuntu installed on a live USB (as-well as dual-booted on my main computer with win7) and this live USB doesn't recognize the right resolution of a particular computers' monitor so I have made a script which (theoretically) all I need to do is double click it to fix the screen for this one monitor's config.
Now the issue is that I cannot for the life of me figure out why it won't work. when I run it (it has xrandr commands in it) it tells me the usage for it.
Anyway, enough babbling. Here it is:
```

#! /bin/bash

cvt 1280 1024 60 | tail -c -82 > temp.txt
xrandr --newmode < temp.txt
xrandr --addmode VGA1 "1280x1024_60.00"
xrandr --output VGA1 --mode 1280x1024_60.00
rm temp.txt


```

Here is what it outputs when I run it:

```
ubuntu@ubuntu:~$ ./Desktop/1280x1024.sh
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>

```

So any suggestions?
I am open to bad practice corrections or alternate ways to do the same thing if you know of any :D

---

### Post by GeorgeVita on 2011-03-28
Hello **hydrox24**,
the problem is that your **xrandr** command uses all characters from temp.txt file and not just the parameters.
('Modeline' is not used by xrandr command)
Try your steps manually (terminal) to find out where is the problem (use the parameters AFTER 'Modeline').

I used the following procedure to create a 1200x800 mode for my DVI connected monitor:
(use below commands with care, read **man** pages before!)

```

g@gPC:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+
   1152x864       75.0  
   1024x768       75.1     75.0     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)
g@gPC:~$ xvidtune -show
"1280x1024"   108.00   1280 1328 1440 1688   1024 1025 1028 1066 +hsync +vsync

g@gPC:~$ cvt 1200 800 60
# 1200x800 59.86 Hz (CVT) hsync: 49.74 kHz; pclk: 78.00 MHz
Modeline "1200x800_60.00"   78.00  1200 1264 1384 1568  800 803 813 831 -hsync +vsync
g@gPC:~$ xrandr --newmode "1200x800" 78 1200 1264 1384 1568  800 803 813 831 -hsync +vsync
g@gPC:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+
   1152x864       75.0  
   1024x768       75.1     75.0     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)
  1200x800 (0x119)   78.0MHz
        h: width  1200 start 1264 end 1384 total 1568 skew    0 clock   49.7KHz
        v: height  800 start  803 end  813 total  831           clock   59.9Hz
g@gPC:~$ xrandr --addmode DVI-0 "1200x800"
g@gPC:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+
   1152x864       75.0  
   1024x768       75.1     75.0     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
   1200x800       59.9  
S-video disconnected (normal left inverted right x axis y axis)
g@gPC:~$ xrandr --output DVI-0 --mode 1200x800
g@gPC:~$ xrandr
Screen 0: minimum 320 x 200, current 1200 x 800, maximum 8192 x 8192
DVI-0 connected 1200x800+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +
   1152x864       75.0  
   1024x768       75.1     75.0     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
   1200x800       59.9* 
S-video disconnected (normal left inverted right x axis y axis)
g@gPC:~$ xrandr --output DVI-0 --mode 1280x1024
g@gPC:~$ xvidtune -show
"1280x1024"   108.00   1280 1328 1440 1688   1024 1025 1028 1066 +hsync +vsync
g@gPC:~$ 
```

Below is the list of commands to set/test new mode without command's output:
```

g@gPC:~$ xrandr
g@gPC:~$ xvidtune -show
g@gPC:~$ cvt 1200 800 60
g@gPC:~$ xrandr --newmode "1200x800" 78 1200 1264 1384 1568  800 803 813 831 -hsync +vsync
g@gPC:~$ xrandr
g@gPC:~$ xrandr --addmode DVI-0 "1200x800"
g@gPC:~$ xrandr
g@gPC:~$ xrandr --output DVI-0 --mode 1200x800
g@gPC:~$ xrandr
g@gPC:~$ xrandr --output DVI-0 --mode 1280x1024
g@gPC:~$ xvidtune -show

```

Regards,
George

P.S. all above tested on a fully updated Ubuntu 10.04 (2.6.32-30-generic #59-Ubuntu)

---

