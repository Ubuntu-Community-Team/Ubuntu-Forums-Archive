---
title: "unity freezes system after clicking on &quot;monitors&quot;"
date: 2011-04-30
forum: General Help
---

### Post by awambawamb on 2011-04-30
Hi guys,
the problems is exactly the one in the title. I was trying to tweak my screen resolution but when i clicked on "monitor" the computer froze. No response from keyboard or other buttons.
my machine is a (don't laugh!) hp pavilion zd8369ea.
thanks
Max

---

### Post by teachop on 2011-04-30
> **awambawamb said:**
> Hi guys,
the problems is exactly the one in the title. I was trying to tweak my screen resolution but when i clicked on "monitor" the computer froze. No response from keyboard or other buttons.
my machine is a (don't laugh!) hp pavilion zd8369ea.
thanks
Max
Do you have to go for the "big switch" when this happens?  I wonder what you would see from the Terminal with the command:  "xrandr --verbose", which should show the possible modes.  Maybe when xrandr runs it will cause a lock-up too, and I hate to do that to you again!  Google xrandr, and see if you think it would be worthwhile to start in that direction.

---

### Post by awambawamb on 2011-05-02
here is the output of the command:

```
awambawamb@zd8000:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x51
	Timestamp:  18314
	Subpixel:   no subpixels
	Clones:     S-video
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	load detection: 1 (0x00000001)	range:  (0,1)
LVDS connected 1440x900+0+0 (0x54) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x52
	Timestamp:  18314
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	scaling mode:	Full
		supported: None         Full         Center       Full aspect 
  1440x900 (0x54)   96.3MHz *current +preferred
        h: width  1440 start 1504 end 1536 total 1760 skew    0 clock   54.7KHz
        v: height  900 start  903 end  906 total  912           clock   60.0Hz
  1280x854 (0x55)   89.2MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock   53.1KHz
        v: height  854 start  857 end  867 total  887           clock   59.9Hz
  1280x800 (0x56)   83.5MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  803 end  809 total  831           clock   59.8Hz
  1280x720 (0x57)   74.5MHz -HSync +VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   44.8KHz
        v: height  720 start  723 end  728 total  748           clock   59.9Hz
  1152x768 (0x58)   71.8MHz -HSync +VSync
        h: width  1152 start 1216 end 1328 total 1504 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1024x768 (0x59)   63.5MHz -HSync +VSync
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
  800x600 (0x5a)   38.2MHz -HSync +VSync
        h: width   800 start  832 end  912 total 1024 skew    0 clock   37.4KHz
        v: height  600 start  603 end  607 total  624           clock   59.9Hz
  848x480 (0x5b)   31.5MHz -HSync +VSync
        h: width   848 start  872 end  952 total 1056 skew    0 clock   29.8KHz
        v: height  480 start  483 end  493 total  500           clock   59.7Hz
  720x480 (0x5c)   26.8MHz -HSync +VSync
        h: width   720 start  744 end  808 total  896 skew    0 clock   29.9KHz
        v: height  480 start  483 end  493 total  500           clock   59.7Hz
  640x480 (0x5d)   23.8MHz -HSync +VSync
        h: width   640 start  664 end  720 total  800 skew    0 clock   29.7KHz
        v: height  480 start  483 end  487 total  500           clock   59.4Hz
S-video disconnected (normal left inverted right x axis y axis)
	Identifier: 0x53
	Timestamp:  18314
	Subpixel:   no subpixels
	Clones:     VGA-0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	tv standard:	ntsc
		supported: ntsc         pal          pal-m        pal-60      
		           ntsc-j       scart-pal    pal-cn       secam       
	load detection: 1 (0x00000001)	range:  (0,1)
```

---

