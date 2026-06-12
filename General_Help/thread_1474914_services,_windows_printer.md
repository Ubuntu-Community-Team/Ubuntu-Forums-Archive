---
title: "services, windows printer"
date: 2010-05-06
forum: General Help
---

### Post by jgw on 2010-05-06
I just installed 10.04 (64 bit) and am trying to get stuff setup.  I am trying to setup access to my windows printer. 

I have connected to my windows network, can see the directories and Print$ but cannot see my printer that I had setup under the previous iteration.  I started rooting around and in system/administration/printing I thought I would troubleshoot and it told me that cups was not running and to goto system/administration/services and there is no services listed (problem 1)

My other thing is what is the print$ in the network.  It seems to be the files to run the printer but there is no printer shown.  I am, obviously, confused.

I may also be trying to setup the printer all wrong so if somebody could point me in the right direction?

Any thoughts on this stuff would be appreciated................

---

### Post by jgw on 2010-05-07
I setup my windows printer.  It turned out to be pretty simple.  system/administrator/printing.  Add new printer.  find network printer (had to put in the ip of the windows computer that had the shared printer (run 'ipconfig' on the windows machine to get that)).  The printer was an canon ip4200.  I then told the program that it was a canon and it popped up all known canon printers and asked me to choose so it could install the drivers.  Its now a done deal!

I did not get a message telling me that cups wasn't running but I just reinstalled it as per another thread that I had read.

I no longer need to know just what the "print$" folder was.  I no longer need the "systems" under system/administrator so I don't mind that its missing.  

I guess I solved my own problem!  (things are not all bad!)

---

