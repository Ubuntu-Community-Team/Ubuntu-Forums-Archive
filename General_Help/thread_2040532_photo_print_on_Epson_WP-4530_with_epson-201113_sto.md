---
title: "photo print on Epson WP-4530 with epson-201113 stops"
date: 2012-08-11
forum: General Help
---

### Post by jejones3141 on 2012-08-11
I have an Epson WP-4530, and find myself having to print a photograph on it.

The printer simply will not feed photo paper through the main tray, and the epson-escpr driver doesn't let one select the rear paper feed, so I went to openprinting.org and got epson-201113w (the 64-bit .deb), installed it, and set the printer up to use epson-201113w. (I am a bit curious about why epson-201113w isn't in the Ubuntu repositories, but that's another issue.)

Sure enough, there's the knob to twist for paper source. I had already gone to the printer itself and told it the rear tray is active, so I fire up GIMP, open an image, configure it so it prints out 8 x 10, photo paper, and print... and the print job goes into "stopped" state, seemingly before a significant amount of data goes out to the printer.

I can still print on the regular paper in the main paper tray, but I do need to print the photo.

One thing I notice--epson-201113w's paper choices for anything but plain vanilla paper are all "Epson ...". I've noticed some photo paper in the past that had a bar code on the non-print side that some printers apparently read; is epson-201113w perhaps set up to only work with Epson paper?

---

