---
title: "Screen resolution suddenly changed to 800x600"
date: 2009-10-27
forum: General Help
---

### Post by TideMan on 2009-10-27
When I booted up today, my screen resolution had suddenly reduced to 800x600 and I don't seem to be able to increase it.  I'm running Ubuntu 8.04.

Here's what I get when I do: 
> ~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)


and here's what I get when I do:
> ~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  


and here's an excerpt from xorg.conf:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"DELL E172FP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection


Can anyone tell me what is going on?
And how I fix it?

---

