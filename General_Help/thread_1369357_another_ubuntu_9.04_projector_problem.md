---
title: "another ubuntu 9.04 projector problem"
date: 2009-12-31
forum: General Help
---

### Post by rajan on 2009-12-31
hi guys, i'm in a pinch and i really need your help getting my laptop to work with a projector.

i've tried everything... starting the laptop with the projector attached and on, reconfiguring the x server with the projector attached, fn+f8, and probably about 10 other things. 

here is the relevant information:

```

rajan@saraswati:~$ lspci | grep VGA 
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1) 
rajan@saraswati:~$ xrandr -q --verbose 
Screen 0: minimum 640 x 350, current 1280 x 960, maximum 1280 x 960 
default connected 1280x960+0+0 (0x123) normal (normal) 0mm x 0mm 
	Identifier: 0x122 
	Timestamp:  26975 
	Subpixel:   no subpixels 
	Clones:    
	CRTC:       0 
	CRTCs:      0 
	Panning:    0x0+0+0 
	Tracking:   0x0+0+0 
	Border:     0/0/0/0 
	Transform:  1.000000 0.000000 0.000000 
	            0.000000 1.000000 0.000000 
	            0.000000 0.000000 1.000000 
	           filter: 
  1280x960 (0x123)   92.2MHz *current 
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   72.0KHz 
        v: height  960 start    0 end    0 total  960           clock   75.0Hz 
  1280x960 (0x124)   73.7MHz 
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   57.6KHz 
        v: height  960 start    0 end    0 total  960           clock   60.0Hz 
  1152x864 (0x125)   84.6MHz 
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   73.4KHz 
        v: height  864 start    0 end    0 total  864           clock   85.0Hz 
  1152x864 (0x126)   74.6MHz 
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   64.8KHz 
        v: height  864 start    0 end    0 total  864           clock   75.0Hz 
  1152x864 (0x127)   69.7MHz 
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   60.5KHz 
        v: height  864 start    0 end    0 total  864           clock   70.0Hz 
  1152x864 (0x128)   59.7MHz 
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   51.8KHz 
        v: height  864 start    0 end    0 total  864           clock   60.0Hz 
  1024x768 (0x129)   47.2MHz 
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   46.1KHz 
        v: height  768 start    0 end    0 total  768           clock   60.0Hz 
  1024x768 (0x12a)   66.8MHz 
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   65.3KHz 
        v: height  768 start    0 end    0 total  768           clock   85.0Hz 
  1024x768 (0x12b)   59.0MHz 
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   57.6KHz 
        v: height  768 start    0 end    0 total  768           clock   75.0Hz 
  1024x768 (0x12c)   55.1MHz 
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   53.8KHz 
        v: height  768 start    0 end    0 total  768           clock   70.0Hz 
  832x624 (0x12d)   38.9MHz 
        h: width   832 start    0 end    0 total  832 skew    0 clock   46.8KHz 
        v: height  624 start    0 end    0 total  624           clock   75.0Hz 
  800x600 (0x12e)   40.8MHz 
        h: width   800 start    0 end    0 total  800 skew    0 clock   51.0KHz 
        v: height  600 start    0 end    0 total  600           clock   85.0Hz 
  800x600 (0x12f)   36.0MHz 
        h: width   800 start    0 end    0 total  800 skew    0 clock   45.0KHz 
        v: height  600 start    0 end    0 total  600           clock   75.0Hz 
  800x600 (0x130)   34.6MHz 
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.2KHz 
        v: height  600 start    0 end    0 total  600           clock   72.0Hz 
  800x600 (0x131)   28.8MHz 
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.0KHz 
        v: height  600 start    0 end    0 total  600           clock   60.0Hz 
  800x600 (0x132)   26.9MHz 
        h: width   800 start    0 end    0 total  800 skew    0 clock   33.6KHz 
        v: height  600 start    0 end    0 total  600           clock   56.0Hz 
  640x480 (0x133)   26.1MHz 
        h: width   640 start    0 end    0 total  640 skew    0 clock   40.8KHz 
        v: height  480 start    0 end    0 total  480           clock   85.0Hz 
  640x480 (0x134)   23.0MHz 
        h: width   640 start    0 end    0 total  640 skew    0 clock   36.0KHz 
        v: height  480 start    0 end    0 total  480           clock   75.0Hz 
  640x480 (0x135)   22.4MHz 
        h: width   640 start    0 end    0 total  640 skew    0 clock   35.0KHz 
        v: height  480 start    0 end    0 total  480           clock   73.0Hz 
  640x480 (0x136)   20.6MHz 
        h: width   640 start    0 end    0 total  640 skew    0 clock   32.2KHz 
        v: height  480 start    0 end    0 total  480           clock   67.0Hz 
  640x480 (0x137)   18.4MHz 
        h: width   640 start    0 end    0 total  640 skew    0 clock   28.8KHz 
        v: height  480 start    0 end    0 total  480           clock   60.0Hz 
  720x400 (0x138)   25.3MHz 
        h: width   720 start    0 end    0 total  720 skew    0 clock   35.2KHz 
        v: height  400 start    0 end    0 total  400           clock   88.0Hz 
  720x400 (0x139)   20.2MHz 
        h: width   720 start    0 end    0 total  720 skew    0 clock   28.0KHz 
        v: height  400 start    0 end    0 total  400           clock   70.0Hz 
  720x400 (0x13a)   24.5MHz 
        h: width   720 start    0 end    0 total  720 skew    0 clock   34.0KHz 
        v: height  400 start    0 end    0 total  400           clock   85.0Hz 
  640x400 (0x13b)   21.8MHz 
        h: width   640 start    0 end    0 total  640 skew    0 clock   34.0KHz 
        v: height  400 start    0 end    0 total  400           clock   85.0Hz 
  640x350 (0x13c)   19.0MHz 
        h: width   640 start    0 end    0 total  640 skew    0 clock   29.8KHz 
        v: height  350 start    0 end    0 total  350           clock   85.0Hz 
rajan@saraswati:~$ xrandr 
Screen 0: minimum 640 x 350, current 1280 x 960, maximum 1280 x 960 
default connected 1280x960+0+0 0mm x 0mm 
   1280x960       75.0*    60.0  
   1152x864       85.0     75.0     70.0     60.0  
   1024x768       60.0     85.0     75.0     70.0  
   832x624        75.0  
   800x600        85.0     75.0     72.0     60.0     56.0  
   640x480        85.0     75.0     73.0     67.0     60.0  
   720x400        88.0     70.0     85.0  
   640x400        85.0  
   640x350        85.0  

```

as you can see, xrandr doesn't recognize the projector when it is connected, and it only shows my default (laptop lcd) monitor. 

when i press fn+f8 i get a pop-up that says "Could not switch the monitor configuration could not find a suitable configuration"

If anyone can help me and allow me to avoid using the nvidia driver, which totally toasted my system a few months back when i tried it, i would really appreciate it. happy new year!

---

### Post by rajan on 2010-01-07
still really need help on this problem. i tried installing the nvidia driver, but my computer got so slow that i couldn't even run openoffice. fortunately it didn't lock up like it did before, but i still can't use it for this presentation without some help getting the projector to work. with the nvidia driver, the projector worked, but like i said, i can't use it. 

thanks!

---

