---
title: "Recommended FOO* driver stuck in Monochrome for Samsung CLP-315W Printer in Karmic"
date: 2010-03-09
forum: General Help
---

### Post by karat on 2010-03-09
I just set up a Samsung CLP-315W printer on my Karmic Koala Ubuntu system.

I can find the printer, but the printer colors are swapped in color mode.
As a result, I put the driver (the recommended FOO* driver) in monochrome mode under printer options and applied them.

Recently, I had a map to print where the wrong colors didn't matter, so I put it in color mode under printer options in the driver GUI.  However, even after applying the changes, the printer is stuck in monochrome.

Some notes on the "wrong colors" issue:
The user manual claims this is a common Linux problem:
"Some color images come out in unexpected color"
"This is a known bug in Ghostscript (until GNU Ghostscript version 7.xx) when the base color space of the document in indexed RGB color space and it is converted through CIE color space. Because Postscript uses CIE color space for Color Matching System, you should upgrade Ghostscript on your system to at least GNU Ghostscript version 8.xx or later. You can find recent Ghostscript versions at www.ghostscript.com."
I am running Ghostscript 8.7x, but I still have this problem.

---

