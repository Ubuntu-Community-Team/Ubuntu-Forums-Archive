---
title: "Ubuntu won't detect VGA connected TV"
date: 2009-12-16
forum: General Help
---

### Post by tylersontag on 2009-12-16
Hey all, I’m building a media center out of an old desktop (which has turned into discovering all the components are bad and basically bareboning a new computer &#61514; )to hook into my new Sharp 42’’ LCD TV ([http://www.sharpusa.com/ForHome/HomeEntertainment/LCDTVs/LC42SB45UT.aspx](http://www.sharpusa.com/ForHome/HomeEntertainment/LCDTVs/LC42SB45UT.aspx)) and I’m having a problem getting 9.10 to detect it.

I had an old CRT that I did the install on and it detected it fine (Display shows 16’’ Whatever Monitor)  and even loaded with support up to 1100~x900~ resolution.  Now if after a boot I just plug in my TV it looks fine, displays fine.

However, when I reboot with the TV hooked up, it boots to 800x600 and the display panel shows “Unknown Device”   So I’ve been using xrandr just to manually add the resolutions I want but I have to do it every boot.  Im using my motherboards integrated Intel GMA X4500 video card and haven’t installed anything special in the way of drivers past a fresh install of Ubuntu 9.10, it looks good, runs compiz fine.   I suppose in my startup file I could just put the 3 commands that create/add/set the resolution but that seems kinda hacky.  Any ideas?

And, on a lesser note, you’ll notice on that TV’s page, it claims Full HD 1080p (1920 x 1080) Resolution.  But when I use xrandr to set that resolution (60 and 120 Hz) it won’t display and says to drop it down to 1600x1400.  I’m running this through a VGA cord, maybe it can only take 1920x1080 through an HDMI cord, I don’t know, just thought I’d toss that out there too.  Thanks for any help, im pushing 2 years since I dropped windows and went 100% Ubuntu (minus a virtual box of XP) and lovin it.

---

### Post by Kylerobhew1 on 2010-01-18
i need help with this too my toshiba regza does the same thing why cant we just disable monitor detection and make the driver automatically display all of the modes that your CARD supports and not what ubuntu THINKS your MONITOR can use. Im sick Of buying hardware just to have you guys screw everything up. you would think if anyone was gonna get xorg rite it would be ubuntu, for the record all of my drivers are up to date and working properly its just your stupid @$$ detection setting, heres a tip for the dev's, if a monitor is going to come up as unknown make all modes supported not just 800x600 and below at 60hz by the gfx cards and not the monitors, after all we paid for our hardware not you guys. >:-(

---

### Post by Kylerobhew1 on 2010-01-18
excuse my half drunken pissedoffedness but this really frustratesthecrap out of me, and i think more than half of the community would agree that you have taken a serious downturn with your new release, what happened you used to be considered more stable than mac now i wouldn't even call you pc stable any more what with how sloppy your new os is

---

