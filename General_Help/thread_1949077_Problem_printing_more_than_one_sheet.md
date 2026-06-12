---
title: "Problem printing more than one sheet"
date: 2012-03-29
forum: General Help
---

### Post by Handssolow on 2012-03-29
If I want to print a second sheet of a document I have to reboot my desktop PC. The first sheet is printed normally and a normal message appears saying the job has finished. If I attempt to print a second sheet, a box appears saying "Printing" etc and the Document Print Status (my jobs) shows the Status as processing but that's all I get, the second sheet isn't printed, the printer remains quiet.

Yet if I reboot just the PC, before I've even re-logged in the printer fires up and prints the second sheet. For a 3rd sheet I'd have to reboot.

I changed my motherboard in the past few months and as it doesn't have a printer port, I am having to use a converter cable (centronics parallel to USB). The printer is a Canon BJ300 though I have configured Ubuntu 11.10 to see it as a BJ200. I have run it this way for years because calling it a BJ200 worked whilst configuring it as a BJ300 it printed garbage. I haven't tried correctly configuring it as a BJ300 with the new motherboard.

If I get stuck I could fit a PCI I/O card which will have a printer socket but can I get proper printing without resorting to this solution? Is the problem with having the converter cable?

edit: I notice others are reporting something similar with libreoffice but I get single sheet printing with a pdf document.

---

### Post by Handssolow on 2012-05-08
With no suggestions offered here and this problem not solved, I bought a PCI parallel port card, it was cheap enough. Initially my Canon printer still wasn't recognised by CUPS though at least the parallel port card was found. The correct kernel modules seemed to be loaded but not the printer driver.

Using [http://localhost:631](http://localhost:631) in a fresh Firefox window to bypass my Script blocker settings, I got to add my printer as a BJ200 and once I'd allowed cookies. Printing seems back to normal. I can't really mark this thread as solved because it wasn't, I had to buy a PCI parallel card instead of using my parallel to usb converter cable.

I'm not sure why CUPS couldn't find my printer using System Settings>Printers, perhaps it's because my BJ300 dates from the last century? ...or is there some bug in the normal process used to install a new printer?

---

### Post by Handssolow on 2012-06-24
I've still got a problem with printing using my old Canon parallel port printer with a more modern motherboard which has only USB sockets. Apparently Msoft specified that parallel ports would become obsolete, hence their demise I suppose.

I haven't needed to print anything recently until today and I discover that no printer is shown in printer manager. After attempting to configure the parallel card again, I get one of the 6 CPU cores running at 100%, as had happened too 3 weeks ago. I posted my findings and reported that a kernel upgrade then cured this 100% CPU problem here, I didn't check though until today if my printer still worked.
[http://ubuntuforums.org/showthread.php?t=1986433&page=2](http://ubuntuforums.org/showthread.php?t=1986433&page=2)

Making no progress today I concluded that the PCI parallel card was either faulty or incompatible and so I reverted back to using the Prolific 2305 based parallel to USB cable.

I'm back where I started. From a fresh cold reboot I can print only one sheet. A second print job stalls. There's enough in launchpad to suggest it's a parallel-USB problem rather than CUPS.

Any suggestions other than one from a family member who says I should buy a modern printer?

---

