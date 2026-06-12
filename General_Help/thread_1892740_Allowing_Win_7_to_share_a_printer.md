---
title: "Allowing Win 7 to share a printer"
date: 2011-12-08
forum: General Help
---

### Post by DrBob89 on 2011-12-08
I have a desktop computer running Ubuntu 11.04 with an attached Canon multifunction printer and ext hard drive.  I have a laptop running Ubuntu that shares files and the printer.

I recently bought my wife a laptop running Win7.  I have successfully configured it to share files and to back up to the  external drive on the desktop computer, but I cannot get it to recognize the printer.  Any thoughts?

Bob

---

### Post by lechien73 on 2011-12-08
Hi,

I had a similar issue.  Most of my machines are Ubuntu, but I had one Windows XP machine that needed to print to it.

I used the instructions at [this link]("http://www.liberiangeek.net/2010/12/share-printer-ubuntu-10-0410-10-maverick-meerkat-windows-print/") to get it working.

The only change I made was setting setting "guest ok" to "yes" in smb.conf

---

### Post by Francis4344 on 2011-12-09
Well, first of all, congrats for making WIN7 share anything with Ubuntu. I have not manage that yet!

Can your printer be a network printer? It might be easier to share if the printer has it's own IP address on the network instead of going through Ubuntu. 

I never has a Canon, I always buy HP. For example, HP does supply HPLIP, a software for it's printer on Linux altough HP does not offer support other that self serve. 

Sorry I can't help you. Hopefully, better minds will chime in!:D

---

### Post by DrBob89 on 2012-02-20
Well, it took me this long to make it work, but the link above works with the following tweak.

Windows uses the username and password used to log in to windows to validate the printer permissions, therefore the same username and password has to exist on the Linux machine being used as the print server.  Once you have made that alteration,  Win7 automatically detects the printer on the server if you have set it to be shared and the rest is a piece of cake.

---

