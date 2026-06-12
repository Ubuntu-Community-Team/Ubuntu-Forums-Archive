---
title: "Difficulty printing to HP1410 over wireless network"
date: 2009-07-23
forum: General Help
---

### Post by Upkeep on 2009-07-23
Hi everyone - it's my first post, so please be gentle!  I'm running Ubuntu 8.10 on an HP2133 mini-note netbook and so far pretty much everything is running very nicely.  Can't get the built in mic to work, but never mind.

This is my first Linux machine, but I'm reasonably skilled with Windows XP.

Enough waffle.  I have an HP1410 printer/scanner/copier attached by USB to a Windows XP box and I have access to the XP box via a Linksys WRT54GS wireless router.

System>Administration>Printing reveals my printer with the following URI "smb://MSHOME/STUDY/HPPSC140".  Status is listed as idle.  When I try to print a test page the printer kicks off and appears to be about to print.... but... it gives up the ghost the power light begins to flash intermittently and if I open the printer queue on the XP box, I get the following (sorry to type it out longhand - I don't have a pic)

Document name: Remote Downlevel Document
Status: Printing
Owner: Guest
Pages: N/A
Size: 64.0KB/7.25MB
Submitted: 19:00:19 7/23/2009
Port: USB003

That's as far as it gets - the 64.0KB/7.25MB stays that way (7.25MB seems awfully large for a test page) and no printout arrives.  It's frustratingly close - but I am at a loss as to what to do next.

Can anyone who is a printer wizard help me out?

Thanks
Upkeep:confused:

---

### Post by Upkeep on 2009-08-01
Well, I know it's usually bad form to reply to one's own posts, but as I managed to sort out my problem I thought I should at least say how in case someone else comes this way.

Firstly I downloaded and installed HPLIP from [http://hplipopensource.com/hplip-web/models/psc/psc_1400_series.html](http://hplipopensource.com/hplip-web/models/psc/psc_1400_series.html)

I took my mini-note to the printer and connected via USB.  Set up ran perfectly and I got a nice test printout.

Back to Samba.  Turns out it was the foomatic driver that wasn't up to scratch.  What worked was:

Printers>New>Windows printer via Samba>Browse[selected HP1400 HP PSC 1400 series]>OK[URI box now populated]>Forward[Searching for drivers]

Here I had the choice of using the foomatic driver or highlighting the Provide ppd file radio button.  This I did, navigated to the appropriate HP1400 ppd file that came with the HPLIP download and used that instead.

Printer make and model now shows as HP PSC1400 Series, HPCUPS 3.9.6b4 and out comes a nice pretty Ubuntu test page  Job done.

Upkeep

---

### Post by Sed Levis on 2011-10-15
Thank you for this.  I'm glad you posted your fix when there wasn't much help given to you.  I am experiencing the same problem with the exception that I'm trying to print through Win 7.  I'm going to rant for the next few lines.  Feel free to skip them.

Oh dear Great Magnet in the sky, why do you hate humanity so much?  Why do you make print drivers so frustrating. Why must you insist that the pitiful carbon based turd machines we call humans insist on believing that software is useless unless it's sold to make millions thus creating an atmosphere that causes the problems I'm having.  Hey, Great Magnet, I've blown several hours trying to get a graph from Libreoffice to print through a windows 7 machine.  Why can't these things play nice?

Anyway, I digress.  So, I have a Dell Latitude D620 running Ubuntu 11.10 and I followed your procedure.  Unfortunately, I'm getting the same problems (mostly).  Anyway, no printing from the dell and it locks up the spooler on the win7 machine each time I try to print from the dell making me want to kill myself.

I'm a little drunk at this point and I really need to get this fixed by Thursday so I can turn in my lab report.  Would anyone be willing to tell me what questions I should be asking and how to ask them?  Then, would anyone else (possibly the same person) be willing to answer the properly parsed questions?

Thanks!

I'm off to bed. :confused:](*,)#-o <--these are dumb fun.

---

