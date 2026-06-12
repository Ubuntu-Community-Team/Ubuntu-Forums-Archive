---
title: "Why is i810 driver better than vesa? Also 855resolution vs. 915resolution?"
date: 2006-02-18
forum: General Help
---

### Post by hyperpsyched on 2006-02-18
I have been using the i810 driver to run the graphics on my Intel 915GM chipset but just as a ruse switched to the vesa driver and saw no real difference in the quality of my display. I am running the 915resolution hack and can only get the 1440x900 in a 1.6 ratio resolution to function. I can get this with either i810 or vesa but vesa gives me the two other standard resolutions as well. 

So my questions is, is there any difference in the quality of the display produced between these two drivers?

More colors, refresh rate? Can anybody tell me why I should run i810 instead of vesa when the 915resolution hack gives me the resolution I need with vesa?

Also, I have had no luck with a 1280 x 800 res on my lappie display. In windows this res is not an option. I tried to force this res using 915resolution but no go. Is it possible that my display and/or bios simply cannot support arbitrary 1.6 ratio resolutions? 1280 x 800 (or 768?) seems pretty standard to me though.

And if you have read this far you can probably tell me what the difference between 855resolution and 915resolution is. Is one better somehow?

---

### Post by Milamber_Cubed on 2006-02-19
AFAIK the vesa driver doesn't support dri whereas the i810 driver does... I am sure someone will correct me if I am wrong :) try running 

glxgears -printfps

in a terminal with both drivers and see if there is a difference. I am sure that there are probably other differences as well - the i810 driver "just works" for me so I haven't really looked into it.

---

### Post by alamba on 2006-02-19
The vesa driver lags in display capabilities heavily as compared to the i815/i915 drivers. Ok..i know that's a very generalistic statement however the biggest lag I've realised is while playing DVD's on my laptop with vesa driver.

To fix your display you might want to look into modeline in google. It took me some doing but was eventually able to get 1800x768 on my laptop using vesa and modeline.

A

---

