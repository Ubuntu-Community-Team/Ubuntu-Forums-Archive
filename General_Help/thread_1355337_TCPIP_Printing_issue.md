---
title: "TCP/IP Printing issue"
date: 2009-12-14
forum: General Help
---

### Post by acrumbacker on 2009-12-14
I am running Ubuntu 9.10.  I incrementally upgraded from Hardy.  I have a Lexmark Optra Lxi+ laserprinter setup on my network with a fixed IP address.  Under Hardy, I printed everything that came up with no problems AND it was Fast.  

It seems the newer versions just dont have the same printing code somewhere because under Karmic it is buggy (but better than Ibex).  Specifically, I can print OpenOffice, FireFox and most other documents as expected but PDF files under both Evince and XPDF are slow, slow, slow -- or dont even print at all.  When I ran Hardy, I had no problems regardless of the application.

device URL lpd://192.168.15.70/PASSTHRU
make: Lexmark 4039 10plus Foomatic/Postscript (recommended)

If I print the test page within System Administration it prints as it should.  This is the second time searching for an answer, but I am tired of sending PDF files to my wife's Windows computer just to print a PDF.

---

### Post by jbrown96 on 2009-12-14
What happens if you share the printer in windows, then have Ubuntu use the shared windows printer via samba?

---

### Post by acrumbacker on 2009-12-15
The printer is connected from the router to the network card inside the printer.  I could not consider using a Windows computer to act as my print server.  The software or how the operating system is handling the code appears to be the problem since OpenOffice prints fine but PDF does not.

12/17 update: anyone with a possible solution?

---

### Post by acrumbacker on 2009-12-22
Anyone with any real ideas where the problem might lie or is this a bug that I am doomed to live with as long as I am running Ubuntu?

---

### Post by harphauler on 2009-12-22
I second the question, precisely the same problem on 9.10 and no windoze machine to go to, have to save to my flash drive and go to the neighbors house. OpenOffice, FireFox, Thunderbird all print great and in a reasonable time but tonight discovered Gimp & FSpot no print.  What's up?

---

