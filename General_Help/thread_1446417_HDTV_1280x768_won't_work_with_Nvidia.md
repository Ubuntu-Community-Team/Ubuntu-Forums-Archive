---
title: "HDTV 1280x768 won't work with Nvidia"
date: 2010-04-04
forum: General Help
---

### Post by Semmelweis on 2010-04-04
I'm about to go back to Windows, I have a problem that doesn't seem to have a fix.

I would like my HDTV to display 1280x768 resolution, but after 14+ combined hours of reading and experimenting I can't get that resolution to work. Here are some system details:

*Ubuntu 9.10
*Nvidia 9800+ GTX with the 185 drivers
*HDTV supporting up to 1280x768 at maximum

If it helps, I can't get 1280x768 with either the Nvidia drivers or the generic Ubuntu drivers. 

Any tips are appreciated!

---

### Post by Linuxforall on 2010-04-04
Remove the 185 drivers, they are too old, you can either download latest 195 series driver from nvidia or you can take the easier route and add nvidia vdpau ppa [https://launchpad.net/~nvidia-vdpau/+archive/ppau](https://launchpad.net/~nvidia-vdpau/+archive/ppau) ppa 

in terminal

remove the 185 driver in the hardware applet and then in terminal

sudo add-apt-repository  ppa:nvidia-vdpau/ppa

sudo apt-get upgrade

then in your hardware applet select latest 195 series driver and reboot.

Also install mplayer and smplayer front end which will make it running with VDPAU HD with ease.Make sure to select vdpau in smplayer video configuration.

---

### Post by Semmelweis on 2010-04-04
I have the new 195.36.15 drivers installed, but now the only available resolutions are 640x480 or smaller.    :(

I'm going to mess around with Xrandr some more and see if any other replies come.

---

### Post by Semmelweis on 2010-04-04
Xrandr is no help: 

**jack@jack-desktop**:~$ cvt 1280 768
# 1280x768 59.87 Hz (CVT) hsync: 47.78 kHz; pclk: 79.50 MHz
Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
**jack@jack-desktop**:~$ xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
**jack@jack-desktop**:~$ xrandr
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
  1280x768_60.00 (0x16f)   79.5MHz
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   47.8KHz
        v: height  768 start  771 end  781 total  798           clock   59.9Hz
**jack@jack-desktop**:~$ xrandr --addmode default 1280x768
xrandr: cannot find mode "1280x768"
**jack@jack-desktop**:~$ xrandr --addmode default 1280x768_60.00
**jack@jack-desktop**:~$ xrandr
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
   1280x768_60.00   59.9  
**jack@jack-desktop**:~$ xrandr --output default --mode 1280x768_60.00
xrandr: Configure crtc 0 failed

---

