---
title: "Printing problems in 11.10"
date: 2011-11-13
forum: General Help
---

### Post by styleruk on 2011-11-13
My turn to step onto soap box...12million people use Linux now?  Ubuntu upgrade renders setting up printers a dark art again.  Last version was ok, 10.11 has become impossible again.  I remember early days of SuSe being difficult to set up printers, this is similar.
My old faithful 895cxi printer took 1hr to set up, and it was already plugged in!
Thought I'd plug in another deskjet printer in to set up (5150)...forget it. Nothing there.
Why does it not just recognise that I've stuck something in the USB like, dare I say... Windows does?
I've had to install windows on my daughters PC now as she has some art homework to do today and cannot print anything.  She was getting along with Ubuntu but I just can't be bothered to change it back now.
Shame, it seems Ubuntu has taken a step back with this one and will lose a lot of people. Not me though, I'll keep tinkering with things until it works like it did 6months ago and be happy with that...similar reason as to why I own a classic car!

If anyone has any advice on a fix for this then let me know.

Simon
Ubuntu 10.11 (64bit)

---

### Post by Habeouscorpus on 2011-11-13
Did you enable drivers for the printers? I google my printers to see which ones work. And printers are all about drivers, and you're right. Drivers in linux is a dark art. We don't have the blessing of some major companies. :)

---

### Post by Mark Phelps on 2011-11-14
What worked for me was using CUPS.  Open a browser and enter "localhost:631".  When you get the screen, select Manager Printers -- and see if CUPS sees your printers.

If not, use the option to Add a printer.  CUPS will then do a search for connected printers.  It also has its own library of printer drivers.

It works fine for me with an old Epson inkjet and two HP printers -- both networked.

---

