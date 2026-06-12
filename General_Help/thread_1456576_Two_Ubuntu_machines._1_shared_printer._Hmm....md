---
title: "Two Ubuntu machines. 1 shared printer. Hmm..."
date: 2010-04-17
forum: General Help
---

### Post by Roasted on 2010-04-17
So, how would I do this? I shared the printer out and windows machines on the network can print to it, but I can't seem to connect to it from my Ubuntu machine. I've tried several different combinations of settings I found on google, but nothing flies. How exactly do I do this?

---

### Post by Jerry N on 2010-04-17
Try This:

System>Administration>Printing>Server>Settings and then check the "Show printers shared by other systems" box.  You might have to reboot (I don't remember).  If the printer is not automatically detected, you might try rebooting the server.

Jerry

BTW, be sure that the server is set up to "Publish shared printers connected to this system".
In my case, the server is running Ubuntu 9.10 and the clients are Ubuntu 9.04, Windows XP, and Windows 7.  The last time I tried 10.04 the networking seemed to fall apart after one of the updates.

---

### Post by Roasted on 2010-04-17
Yeah - I can get that far. But how do I add it? I can view the printers shared on the network, but nothing seems to fly when I try to connect to it.

---

### Post by Morbius1 on 2010-04-17
Have you tried this:


Administration > Printing > New  > Other

  In the Enter URI box enter:

ipp://192.168.0.100:631/printers/Linux-Printer-Name

OR

ipp://Machine_name:631/printers/Linux-Printer_name

Changing 192.168.0.100 or Machine_name to whatever it is on the box that has the printer.

---

### Post by itiswhatitis on 2010-04-17
Do you have to add it?   I checked the boxes and did no setup or anything on my wife's laptop.  When she wants to print something, the printer is there.

Edit:  I did check the boxes on the printer properties share it as well, and set the access control so that anyone could print to it.

---

### Post by Roasted on 2010-04-17
Whenever I type in the path, the "forward" box doesn't become active for me to click.

Is it really this much of a headache to share a printer from 1 ubuntu system to another? Really?

---

### Post by itiswhatitis on 2010-04-17
It shouldn't be hard.  I found it easier than Windows.

On each computer:

System->Administration->Printing

Once the printer configuration is up, Click Server and then Settings.  Then check the boxes:
 - Show printers shared by other systems
 - Publish shared printers connected to this system
 - Allow printing from the Internet (Not sure if this is necessary)
 - Allow remote administration

Then Click OK

Next, on the computer that has the printer connected -  right click on the printer and make sure the boxes next to Shared and Enabled are checked.  If they aren't, click on them.

Then click on Properties
 - Under Access Control, set the button to Allow Printing for Everyone...

After about 30 seconds, you should be able to see it without adding anything on the other computer.

Let me know if that helps.

---

### Post by Roasted on 2010-04-17
Okay wait... there's two things I need to understand here.

1 - Do I even need to "connect" to the printer? I went into OpenOffice and typed up a document and hit print and it just... worked. I never connected to it. It just picked up the only available printer (the shared one upstairs on the other Ubuntu machine) as the default. I was thinking with a Windows mind-set that I need to CONNECT to the printer in order to use it.

2 - Do I have to reboot for any changes to take effect? My computer (the Ubuntu box with no printer) was rebooted cause I went into Windows to game for a little bit. Since I rebooted, it works. However I'm not sure if I did something different from a few hrs ago or if it's needed to "refresh" any print settings. Or heck, maybe I tried too soon after I shared the one upstairs and didn't wait long enough.

---

### Post by Jerry N on 2010-04-18
Your computer did what it was supposed to do - found the networked printer and installed the necessary drivers.  You were just trying to make the job too hard!

Windows 7 does a pretty good job of finding and installing printers automatically too.

---

### Post by Roasted on 2010-04-18
But the curve ball is in Windows you need to right click - connect, whereas it seems with Ubuntu it just "finds" the network printers anyway and allows you to connect to them anyway. Is this accurate what I'm seeing??

---

### Post by itiswhatitis on 2010-04-18
You care correct in what you are seeing.  Ubuntu sees any published printers and makes them available to you.

---

