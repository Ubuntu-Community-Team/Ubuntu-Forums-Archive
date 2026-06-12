---
title: "3-component doesn't work Ubuntu 10.04 (wubi)"
date: 2010-07-16
forum: General Help
---

### Post by pyrodood on 2010-07-16
I've been running windows on my htpc for a few years and I really like Linux and Ubuntu, but had windows installed and left it on there cause I had no problems, well recently something got tweaked and windows was running slow.  So i thought I'd run Ubuntu and see if it ran slow, if it did then I would know it was more likely the hardware.

So i mounted the 64bit iso for 10.04 and ran wubi install.  I'm typing on it now, I had to plug in a separate monitor to see it though, previously I had only been using the Plasma with the computer.  

I can't figure out how to get Ubuntu to display on the 3-component output of my motherboard which is a GA-MA69GM-S2H gigabyte motherboard.  It also has DVI and HDMI, though I don't have an HDMI cable around to test that, I do have a DVI to HDMI cable but don't know exactly where is is to test that.  But I think it should work on the 3-component output and I would like to see if anyone can help me out on how I can go about setting that up.
Ati Radeon x1200

xrandr ouput as follows:
[I]$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     75.0     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)[/I]

So does this mean that the computer does not see the DVI or Component Video Output?  Does it mean that the driver currently running doesn't support those outputs?  I went to restricted drivers but it says none in use on system and nothing was available in the window.

Thanks,
John

---

### Post by pyrodood on 2010-07-31
Update, 
I found my DVI to HDMI cable and hooked only that upon boot.
Ubuntu does boot.  But resolution is way too low and not really compatible with the tv as the picture was wavy.  Was able to navigate to monitors and attempted to select a different resolution, I don't think there was a 720p resolution listed.  I know the video card supports that resolution because it works in windows with the dvi to hdmi cable.  
Question would be if i could force it to use the right resolution.

Also next step will be to purchase an hdmi cable and then perhaps ubuntu will display a hdtv correct resoltion.  
Luckily my motherboard has all of these outputs and I'm not stuck with my only option being the DVI to HDMI cable.  Still confused as to why the Component video doesn't work.
Wishing my tv had a vga input on it right about now.

---

