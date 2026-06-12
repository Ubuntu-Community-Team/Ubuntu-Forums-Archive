---
title: "Can't get HP CP125nw to print in colour"
date: 2012-04-15
forum: General Help
---

### Post by ve4cib on 2012-04-15
I have an HP Colour Laserjet cp1025nw, and I simply cannot get it to print anything in colour.  It produces very nice, crisp greyscale pages, and that's it.

I have installed the Foo2zjs driver as per the instructions [here](http://foo2zjs.rkkda.com/).  I've set up the printer using system-config-printer.

Under the "Printer Options" tab there's an option for Colour Mode.  If I select "Monochrome" the printer works just fine (in black-and-white).  If I select "Colour - Using ICM colour profile" the job gets submitted, and dies somewhere between my computer and the printer; no paper ever comes out the other end.

I've been fighting with this problem for a couple of weeks now, and am running out of ideas.  According to [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) the printer is supported, and works in colour.  So what am I doing wrong?

The printer itself is connected to a Windows XP box, which is in turn set up to share the printer over the network.  Not sure if that would make any difference; I can't imagine that it would.

Has anyone else run into this sort of problem?  Any suggestions on what I should try next?  I'd really like to be able to print things in colour from my Linux boxes.

---

### Post by callmemahavir on 2012-04-15
Did you tried printer settings in the printer hardware?
Some printer has control in hardware to change between color and gray scale.

---

### Post by ve4cib on 2012-04-15
The printer prints in colour from WinXP, so it's not an issue with the printer hardware itself.

---

### Post by callmemahavir on 2012-04-16
Type ...
sytem-config-printer in shell prompt.

Click...
Printer options.

Check ...
Check the output mode in the screen.
Check that color output is selected in output mode.

---

### Post by ve4cib on 2012-04-16
> **callmemahavir said:**
> Type ...
sytem-config-printer in shell prompt.

Click...
Printer options.

Check ...
Check the output mode in the screen.
Check that color output is selected in output mode.

Everything on the Printer Properties panel:

Printing Quality: Normal
Color Mode: Color - use ICM color profile
Resolution: 1200x600 dpi
Page size: Letter
Media Source: Auto Source
Media Type: Standard Paper
Copies: 1

Halftone Algorithm: Default
ICM Color Profile: ICM File hp-cp1025.icm
ICM Color Profile Intent: Perceptual Intent

N-Up Orientation: Portrait
N-Up Printing: 1-up


"Colour Mode" has two options: "Monochrome" and "Colour - use ICM colour profile".  If I use "monochrome" the printer prints just fine, but in b/w.  Using "Colour..." results in no paper coming out of the printer at all, and the job just vanishing from the queue.

---

### Post by callmemahavir on 2012-04-16
Goto this URL and download the drivers...

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_cp1025nw.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_cp1025nw.html)

In the page top click Download HPLIP.

In another page again click HPLIP and try installing.

This software may be useful for you for printing.

---

### Post by ve4cib on 2012-04-16
I've tried that, but the HPLIP driver does not show up when using system-config-printer, and the HLPIP tool requires that the printer either be a stand-alone device on the network, or that it be connected directly to my computer.

Neither of those last two options is feasible, as it's a share via a Windows XP box.

---

### Post by callmemahavir on 2012-04-17
Have you tried Installing CUPS...

CUPS is a standard for printing in UNIX like system.

In command prompt type...

sudo apt-get install cups

AND TRY EXPLORING!!!

---

### Post by ve4cib on 2012-04-17
Of course CUPS is installed.

Out of desperation I tried plugging the printer directly into the router and using it as a stand-alone network printer.  That worked, and I could print in colour, but still no luck when the printer is shared from an XP box.  This is a real head-scratcher.

I suppose I'll just have to rearrange the desk to move the printer close enough to the router so an ethernet cable won't be strung across the middle of the room.

---

