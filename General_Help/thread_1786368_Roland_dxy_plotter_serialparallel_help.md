---
title: "Roland dxy plotter serial/parallel help"
date: 2011-06-19
forum: General Help
---

### Post by Yepi on 2011-06-19
Hi, I am trying to get my DXY 980 plotter to run via serial or parallel.

The plotter worked fine with the usb-parallel cable and I had set it up as a generic raw printer and was using Tuxplot, it also worked using Inkcut but for some reason it just stopped working.
The plotter works fine as I have a serial port on my desktop pc and can plot fine but I want to mod it into a laser cutter so I need to control its speed which Tuxplot can do.

I will be moving away from home for a year on a work placement abroad so I cant use my desktop.
 
I have had some 'success' using the usb-serial cable which is pl2303 and ubuntu recognises it fine and shows up under lsusb, the parallel cable also shows up as pl2305.
I use gtkterm and playing around with the settings the best I can get it to do is to print random letters and symbols even though I sent a proper file as a .plt from inkscape. 

I have also tried cutecom with similar results. 
I have a feeling that it was some update to ubuntu or cups that changed things but cant be certain.


Any help would be appreciated

---

### Post by garyinspringhill on 2012-01-21
I suspect your baud rate is off , not sure what your dxy is needing. It may be easier to try each speed setting on the roland till you find the match your usb>serial is putting out.

---

