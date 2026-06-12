---
title: "Stuck with 800x600 unknown monitor"
date: 2011-04-04
forum: General Help
---

### Post by powerinfsuino on 2011-04-04
New Install of 10.10 stuck using 800x600 res due to "Unknown monitor" was working fine in windows.
Been on google hunting for an answer for the last day, Been told to "xrandr"

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  

A little help please :confused:

Still not working ><

---

### Post by powerinfsuino on 2011-04-04
:popcorn:

---

### Post by powerinfsuino on 2011-04-04
:popcorn:

---

### Post by Grenage on 2011-04-04
You're supposed to bump once a day max, not every 40 minutes.

I can't help with xrandr (look [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html/comment-page-2")), but can probably suggest an xorg.conf if that doesn't work.

---

### Post by powerinfsuino on 2011-04-04
Done that one =/ 
This is rather a pain!!!

---

### Post by soulsource on 2011-04-04
Important thing first: 
What graphics card are you using? If I should guess, I'd say you're using the framebuffer driver instead of the one intended for your graphics card...

---

### Post by Imp558 on 2011-04-04
Mine is doing the same thing after the Nvidia driver install script. I'd gladly trade you resolutions, lol. Is there a tool we can load to let us pick the monitor from a list? I even edited my xorg.conf file to add 1024x768 and no good.

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0

---

### Post by Grenage on 2011-04-04
> **Imp558 said:**
> Mine is doing the same thing after the Nvidia driver install script. I'd gladly trade you resolutions, lol. Is there a tool we can load to let us pick the monitor from a list? I even edited my xorg.conf file to add 1024x768 and no good.

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0

Rough guide [here]("http://www.grenage.com/xorg.html") for an xorg config.  Failing that, post your monitor and graphics card make/model, and I'll knock one up tomorrow morning.

---

### Post by tredegar on 2011-04-04
You are not giving us much information, so here are some questions:

What is the exact make and model of your monitor?
What resolution is it capable of?
CRT or flat panel?
How is it connected (SVGA / HDMI etc).

Do you see useful errors or warnings in the file **/var/log/Xorg.0.log** ?

---

### Post by Imp558 on 2011-04-04
Thanks for helping, once I understood the idea I found the monitor specs and edited xorg.conf for my horizsync and vertrefresh. All good now. 
powerinfsuino: write all your changes on paper (before and after) so you can edit the xorg file with nano from the command line should something go wrong and x fails. Then you can at least get back where you started.

---

### Post by powerinfsuino on 2011-04-04
What is the exact make and model of your monitor?- It's old! viglen something 
What resolution is it capable of? Cant tell anymore (ubuntu wont let me see xD)
CRT or flat panel? crt
How is it connected (SVGA / HDMI etc). vga ?

AM not using a gfx card 

Works fine in windows worked fine with ubuntu 9.10, then my grub lost windows so I had to delete it and reinstall ubuntu now it no longer works.

:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied

I can watch movies with vlc and whatnot.

Been reading that link from [Grenage]("http://ubuntuforums.org/member.php?u=263074")

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 02)
sudo ddcprobe
vbe: VESA 3.0 detected.
oem: VIA M3364
vendor: 
product:  
memory: 65536kb
mode: 640x480x256
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x256
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1600x1200x256
mode: 1600x1200x64k
edid: 
edid: 1 1
id: 2110
eisa: ___2110
serial: 00000000
manufacture: 51 2004
input: sync on green, analog signal.
screensize: 31 23
gamma: 2.200000
dpms: RGB, active off, no suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@56 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@60 Hz (VESA)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x1024@60
ctiming: 1024x768@85
ctiming: 800x600@85
ctiming: 640x480@85
dtiming: 640x480@130
monitorname: 
monitorname: CM1772FS
monitorrange: 30-70, 50-135

cvt 1680 1050 60
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

---

### Post by powerinfsuino on 2011-04-05
Still stuck with 800x600 ><

---

### Post by tredegar on 2011-04-05
> Still stuck with 800x600 ><
But you have not answered the questions. For example:
> What is the exact make and model of your monitor?- It's old! viglen something

---

### Post by powerinfsuino on 2011-04-05
> **tredegar said:**
> But you have not answered the questions. For example:

But it was working before :S.
Before in this case being less then two hours.

---

### Post by Grenage on 2011-04-06
I don't have any experience with VIA graphics, but we can have a go.  Still, we'll ideally want the monitor make/model; there should be a label/sticker/code *somewhere* on the unit.

---

