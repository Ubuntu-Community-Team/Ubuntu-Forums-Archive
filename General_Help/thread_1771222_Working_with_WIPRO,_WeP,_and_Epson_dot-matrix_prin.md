---
title: "Working with WIPRO, WeP, and Epson dot-matrix printers"
date: 2011-05-30
forum: General Help
---

### Post by suchetha on 2011-05-30
Let's start with some basic information about this post.

[LIST]
[*]WIPRO  and WeP ([http://www.wepindia.com](http://www.wepindia.com)) are both dot-matrix printers that are becoming increasingly common in the South/SouthEast Asia region
[*]These printers are basically rebranded Epson dot-matrix printers
[*]There is one post that deals with making them work with Ubuntu ([http://ubuntuforums.org/showthread.php?t=1257924](http://ubuntuforums.org/showthread.php?t=1257924)), but it doesn't work.

(the issue is in the "official" rastertowep filter which fails at some point and sends only a few bytes to the printer)
[/LIST]
Note: I am recalling a saga that I faced. If you are too busy to read it, please go down about one PgDn.

Background:
I am helping an organisation migrate from 100% windows to mostly Linux. The past few months have been spent working with them to find the places where Ubuntu fails their requirements, and making it not fail.

So far we have had to deal with recalcitrant CAPT (proprietary Canon Printer system), in-house software that needs WINE to run (and makes me need vodka to deal with), and - the latest problem - dot-matrix printers that no longer have drivers (or perhaps never did)

The printers I am dealing with are Epson LQ2810, LQ300+, and LQ300+II (and then there are the WeP)

"But wait," I hear you yell. "Openprinting.org has the drivers. They have drivers for EVERYTHING."

and yes at [http://www.openprinting.org/printer/Epson/Epson-LQ_300plus2](http://www.openprinting.org/printer/Epson/Epson-LQ_300plus2) there is a forum user that says that he got it working as a 24-pin printer. (the official status is "paperweight" though)

Every trick I tried using the generic 24-pin PPDs only worked half-way. At best the print range was too long, and it would constantly overshoot the page, and since this was using the continuous feed paper, every single page was two pages. (And before you ask, I made sure the page sizes were accurate). We won't talk about the "at worst."

After getting tired of all this, we decided to use SUSE Linux (SLED) instead of Ubuntu. Installed it, plugged in the printers and IT WORKED!! *loud cheers, clinking of glasses*

So we checked to see what the solution was. The easiest one (and the default solution on SLED) was to use the OMNI ([http://omni.sourceforge.net](http://omni.sourceforge.net)) driver/filter system

Unfortunately this driver is not available on either Ubuntu or Debian (not even debian-oldstable)

I was attempting to set up a PPA to build the OMNI from source, when I noticed another driver was listed.

It was a standard/generic 24-pin driver. So I gave it a shot. And it worked under SUSE with the Epson printer. So I copied the PPD file out, and tried running it on Ubuntu. Here are the steps that worked.

**SOLUTION**

[LIST=1]
[*]Download the attached file(s). You will probably just need the 24-pin PPD, but I have also included the 9-pin PPD (which I haven't tested) just in case.
[*]Browse to the CUPS web interface at [http://localhost:631](http://localhost:631)
NOTE: The printer installer system from the GUI will NOT work. It will throw an error and promptly fail
[*]Create the printer listing using the CUPS web interface, and when it asks for a PPD, point it at the one you just downloaded
[*]PROFIT!!
[/LIST]
I hope this helps someone, ANYONE who has been in the same straits I have been.

So man your chips, and may The Source be with you!

---

### Post by khay on 2011-07-19
I have been looking up and down for the 300+II driver. Although I manage to use the IBM dot matrix driver, but it only print the first page and come out an error(I have only tried with pdf file). Can't wait till next week to try it on my friend's office. I, too, am trying to convert my friend's office to use Linux only.

---

### Post by CesarEdu2 on 2012-11-07
Thank you it works great for Epson LQ-1070+ dot-matrix printer in Ubuntu 12.04 32bits.

---

### Post by wildmanne39 on 2012-11-07
Old thread closed.

---

