---
title: "Monitor: Input Signal out of Range"
date: 2011-12-07
forum: General Help
---

### Post by coolcats on 2011-12-07
Ubuntu is giving me the "Input Signal out of range" when I startup. When it does this, I cannot see anything except that. I'm using a ubuntu CD for booting, which works fine. This means I can edit the files. However the ubuntu I have on the hard-drive still comes up with the error. The monitor is a: Hanns*G HW191A Monitor. I've tried a different monitor, which comes up with "cannot read video mode." Thanks!

---

### Post by seawolf167 on 2011-12-07
Since you cannot see anything on either monitor, and you cannot see any display off either boot method (assuming you've tried the live cd, your normal install, etc.), it sounds like your graphics card is dead.


First things first though, check that you have the correct input selected on the monitor! Then check:

[LIST=1]
[*]Verify the monitors work by plugging them into another computer
[*]Verify that the cables are fully plugged in to both the monitor and computer
[*]Check to see if you get any display during POST (any warnings, errors, text)
[*]Check to see if you get any display by entering BIOS (usually by hitting F2, F10, F12 or DEL upon startup)
[*]Try any other display ports you may have on that computer to see if they work (VGA, DVI, HDMI)
[*]Do you have an extra graphics card sitting around? If so, try that and see if you get any display now
[/LIST]
If 1-5 show no display on the monitor and 6 does so a display, then your graphics card is most probably dead.

---

### Post by dandnsmith on 2011-12-07
I don't agree with that diagnosis, I'm afraid.
The messages, particularly the first are symptomatic of a display not being driven properly - as if the graphics card hs been somehow instructed to use a mode which doesn't work. The second message sounds as if the EDID data may have proved inaccessible from that monitor - could be a cable problem.

I agree with looking to see if any messages can be displayed by the BIOS on bootup - that should decide whether the display is capable of some sort of display from the graphics chipset, and whether the chipset is delivering to the monitor (it uses a vary basic mode of display).

---

