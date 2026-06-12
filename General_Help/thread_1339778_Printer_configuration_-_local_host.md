---
title: "Printer configuration - local host"
date: 2009-11-27
forum: General Help
---

### Post by Bartender on 2009-11-27
OK, this is weird.
A friend gave me his old HP Deskjet 5740.  I plugged it into a desktop PC running Karmic.  The printer was recognized and produced a test page upon request.

I then connected the printer to an Acer 5920 laptop running Ubuntu 9.04 and turned the printer on.  The printer was recognized very quickly, faster than I've ever seen.  I went into OpenOffice and printed out a few pages.

Decided to flush the old printers from the printer list.  Went to Administration>Printing, got the "Printer configuration - local host" window but it just sat there empty, then went gray.  I checked top; CPU usage was almost pegged.  As soon as I force quit the stuck window CPU usage dropped back down to the typical 1 or 2%.  Went into Preferences>Default Printer and set that to the HP 5740 but that didn't help.

So the printer works from OpenOffice, but the Printers window is FUBAR.  Anyone know how to go into terminal and remove all printers, or reload the printer configuration application, or something similar?  I've tried restarting the lappy several times with the HP connected to various USB ports and disconnected completely.  No difference.  The Printers utility locks up every time.

---

### Post by Bartender on 2009-11-28
* bump *
I found a few threads that described removing CUPS and reinstalling.
I'd have to go find some broadband.  Anyone think that might work?

Stuck on dial-up at home.  Used the install CD as a source.  

sudo apt-get remove cups
sudo apt-get install cups

Same problem - clicking on "Printers" in Administration gives me a blank window, CPU usage goes thru the roof, window hangs until Force Quit.

---

### Post by XubuRoxMySox on 2009-11-28
I think you will need to have HPLIP installed (available thru Synaptic). It's a very helpful and necessary little tool.

After it's installed, for a graphical interface to it, open a browser and go to [http://localhost:631/](http://localhost:631/)

Click on **Administration** (you'll be asked for username and password) and look for your printer. If it's not installed, there's an **Add Printer** button and you can choose yours from a drop-down menu.

Be sure to mark the thread SOLVED when (and if) it works for you...

-Robin

---

### Post by Bartender on 2009-11-28
Hi, dixie -
I screwed around with this some more.  I apt-get removed cups again, but this time I didn't try to reinstall from CD. The Administration>Printers window came up without hanging the PC.  The taskbar worked and the default icons were present.  It said "Not connected" across the bottom of the window which makes sense I guess since I'd removed cups.

Went to the library and installed HPLIP.  Synaptic identified cups as one of the dependencies needed to install HPLIP. Used the browser address to access cups - nice trick, didn't know about that.  The printers showed up, I removed the one that I wanted to.

Went back to Administration>Printers and it works fine again.  

So, I don't know what happened but everything appears to be working.  The final test will be plugging the Deskjet back in but for now I'm considering this solved, or fixed anyway! :)

---

