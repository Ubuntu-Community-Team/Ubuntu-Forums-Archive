---
title: "Subpixel order"
date: 2010-01-06
forum: General Help
---

### Post by abdulmajid on 2010-01-06
When I was about to change the font rendering settings, I saw that subpixel order which says, RGB, BGR, VRGB and VBGR. What difference does that make if I had to select one of those settings (though RGB is selected by default). I'm just curious to know that color schemes.
thank you for your time...

---

### Post by sedawk on 2010-01-06
Font rendering can be improved if the software knows how
the R-G-B pixels are physically arranged by your monitor.

If the software known the location of the subpixels it
can generate a (mixed RGB) color so that the subpixels are getting
lighter or darker in the correct sequence and direction.
(For smooth fonts the brightness of the "smoothing pixels" is
 more important than the correct color. Therefore you
 can play with colors to get a smoother brightness correction).

Sometimes it is hard to find out the subpixel orientation
off your screen, even with a good magnifying glass.
But if that is the case you might not see any difference in
subpixel rendering anyway ...

---

