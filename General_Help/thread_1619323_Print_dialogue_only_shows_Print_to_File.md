---
title: "Print dialogue only shows Print to File"
date: 2010-11-11
forum: General Help
---

### Post by bmeakings on 2010-11-11
I had a [previous problem]("http://ubuntuforums.org/showthread.php?t=1613620") with CUPS but I think I managed to get it fixed. I've come across another problem - whenever I print, be it from Firefox, Chome, Gedit, evince or anything that brings up the standard print dialogue, I only get the Print to File option and my printer isn't shown.

But  I can print test pages and applications that use their own print dialogue - LibreOffice/OOo and Adobe Reader seem to be able to print, although Adobe Reader saw the printer as just "lp" and couldn't fully identify it. Printer sharing also works, I'm able to print from my WinXP machine on the network. I just can't seem to print locally.

My printer is an Epson Stylus C66 connected by USB. I tried uninstalling it from CUPS and plugging it back in, where Ubuntu immediately recognised and installed it.

---

### Post by bmeakings on 2010-11-14
Update/bump:

I tried deleting/re-adding my printer again and I swear I didn't do anything different, but I'm now able to print from Firefox. Adobe Reader also sees my printer properly. But all other applications still only show the Print to File option.

Edit: I managed to fix it! I saw that there were some files called libprintbackend which sounded like they were related to the problem. I investigated which package they belonged to which was libgtk2.0-0. I did a re-installation of that package and it turns out that the file libprintbackend-cups.so was missing. My printer now shows up in all programs again :) I thought I'll write this down in case anyone else has the same problem.

---

