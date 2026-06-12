---
title: "Incorrect Monitor Size"
date: 2012-01-26
forum: General Help
---

### Post by 64mgb on 2012-01-26
Sorry if this has been covered.  I've searched and found similar issues but nothing that matches mine.  My system (11.10) reports that I have a ViewSonic 23" monitor attached, but it is actually a ViewSonic 24".  Consequently it does not fill the screen.  I'm not sure where to start looking for a resolution.  In other threads responders wanted to see Xorg.conf, so here is mine.  I'm using an "ATI/AMD proprietary FGLRX graphics driver".  Any ideas?

Thanks,
Rich


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by 64mgb on 2012-01-28
Gonna have to give this a bump...anyone have any ideas?

Thanks,
Rich

---

### Post by mcduck on 2012-01-28
Filling the screen is just a question of using the correct *display resolution*, the physical dimensions of your screen are meaningless.

..and if the resolution is already correct for your monitor, just use your monitor's own settings to adjust the picture.

If you don't know what the correct resolution for your display is, you should be able to either check it from the display's manual, or alternatively a quick google search with the exact model should give you such information. If you aren't able to select the correct resolution, that's usually related to missing or non-working graphics card drivers.

---

### Post by 64mgb on 2012-01-28
> **mcduck said:**
> Filling the screen is just a question of using the correct *display resolution*, the physical dimensions of your screen are meaningless.

..and if the resolution is already correct for your monitor, just use your monitor's own settings to adjust the picture.

If you don't know what the correct resolution for your display is, you should be able to either check it from the display's manual, or alternatively a quick google search with the exact model should give you such information. If you aren't able to select the correct resolution, that's usually related to missing or non-working graphics card drivers.

Thanks for the reply mcduck!  My resolution is set to the correct resolution for my screen (1920x1080).  If you are correct there must be something wrong with my monitor.  When it first boots, the visible display is even smaller...about an inch in on all sides.  After I press the 'Auto Image Adjust' button it expands but is still in about 1/4" - 1/2" on all sides.  The adjustment for Horizontal size is grayed out (oddly there is no adjustment for Vertical size).  But what bothers me the most is that it's detected as a 23" display, and appears to be projecting as if it were on a 23" display.  Guess I might just have to live with it...not really a big deal, just sort of annoying.

Rich

---

### Post by mcduck on 2012-01-28
What kind of simply is it? LCD or CRT? What kind of cable are you using to connect to it? And if you can, could you give the exact model so I could take a look if I can find any relevant information about it?

It really doesn't make any difference if the display's physical size is detected correctly, wrongly, or if it's not detected at all. Your graphics card simply sends image data at certain resolution and refresh rate, it doesn't draw a 23" image or 24" image, it draws a 1920x1080 pixel image. :)

---

### Post by 64mgb on 2012-01-28
> **mcduck said:**
> What kind of simply is it? LCD or CRT? What kind of cable are you using to connect to it? And if you can, could you give the exact model so I could take a look if I can find any relevant information about it?

It really doesn't make any difference if the display's physical size is detected correctly, wrongly, or if it's not detected at all. Your graphics card simply sends image data at certain resolution and refresh rate, it doesn't draw a 23" image or 24" image, it draws a 1920x1080 pixel image. :)

Thanks mcduck!  It's a ViewSonic VS12324 24" LCD, connected with an HDMI cable.  In the searching I've done it appears that the VS12324 is sometimes called a VX12324.

Thanks,
Rich

---

### Post by mcduck on 2012-01-28
Since you are using HDMI to connect to the display, it could be because of some overscan setting on etither the display itself, or in your graphics driver's settings (It's been a long time since I'd had Ati/AMD card capable of using fglrx drivers so I really don't remember what kind of options they give you).

Overscan is something mostly related to television use, dating back to the days of the old CRT displays where the edges of the  cathod ray tube's display area weren't actually visible to the viewer and thus the TV image had to have some extra space around it to make sure the viewer didn't miss anything. Graphics drivers and displays still have options for enabling/disabling overscan, as people might need them when using analog connections or connections (or displays) mainly intended for television use.

I'd recommend checking both Catalyst Control Center, and the display's options, in case you find any option related to overscan. Try toggling it to different setting than what you have now. (HDMI is mainly a TV connection type, which might be confusing either your graphics driver or the display itself). Alternatively you could try connecting with a DVI or VGA cable if you have one available.

---

### Post by 64mgb on 2012-01-28
> **mcduck said:**
> Since you are using HDMI to connect to the display, it could be because of some overscan setting on etither the display itself, or in your graphics driver's settings (It's been a long time since I'd had Ati/AMD card capable of using fglrx drivers so I really don't remember what kind of options they give you).

Overscan is something mostly related to television use, dating back to the days of the old CRT displays where the edges of the  cathod ray tube's display area weren't actually visible to the viewer and thus the TV image had to have some extra space around it to make sure the viewer didn't miss anything. Graphics drivers and displays still have options for enabling/disabling overscan, as people might need them when using analog connections or connections (or displays) mainly intended for television use.

I'd recommend checking both Catalyst Control Center, and the display's options, in case you find any option related to overscan. Try toggling it to different setting than what you have now. (HDMI is mainly a TV connection type, which might be confusing either your graphics driver or the display itself). Alternatively you could try connecting with a DVI or VGA cable if you have one available.

Thank you mcduck!  I looked around for a driver app that would allow me to make adjustments like my PCs with Nvidia cards have, but couldn't find anything.  Based on your hint I found the Catalyst Control Center which allows me to adjust the overscan.  Now I have a full screen image!

Thanks a ton!

Rich

---

### Post by mcduck on 2012-01-29
No problem, great that you got it working and with quite an easy solution even. :)

---

