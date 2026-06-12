---
title: "I've broken printing please help"
date: 2011-03-21
forum: General Help
---

### Post by mikehattingh on 2011-03-21
I had been having problems with printing after adding a network printer. I started getting errors from cups, the error alerts would not close. I was poking around and tried deleting some stuff, you know. Now there are no printers in the print manager. Server-> New-> Printer is grayed out and the add button is grayed out. I need to reinstall/ reset printing support. I don't know how to do that.

Printer is connected via usb and has been used on this install.

Thanks for your help

---

### Post by mikehattingh on 2011-03-25
OK no help but I got it back I think. I upgraded to Maverick but that didn't help. I guess CUPS is not replaced/ modified in the update. I spent some time trying to apt-get install --reinstall cups. No luck there because the stop cups task was hanging, stopped it myself by kill -9 #### . Then after the update appeared to finish the start cups task hung. I killed it but then the update was unsuccessful. I also tried to start cups manually and was told it was already running. $ps aux | grep cups sows no cups task running. Nice.

Anyway what I have done is: Copy /etc/cups over from another computer running Lucid. Restart computer. $apt-get install --reinstall cups. Delete the printer in question from the print manager(printer had also been installed on the other computer). Add the printer in question in the print manager. Restart. Print test page. Rejoice :D

Yeah, so don't randomly delete random stuff X)

I can only hope that none of those cups files from my tablet, point to anything they shouldn't on my PC.

---

