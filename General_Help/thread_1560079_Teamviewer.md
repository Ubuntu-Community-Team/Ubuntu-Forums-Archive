---
title: "Teamviewer"
date: 2010-08-24
forum: General Help
---

### Post by ki4jgt on 2010-08-24
Need to get TeamViewer installed on Ubuntu. I've downloaded the .deb, after installing, it doesn't show up anywhere in my menus. Need it for company I'm setting up. Thanks in advanced guys.

---

### Post by X.Cyclop on 2010-08-24
Check **/usr** folder, might be there.

---

### Post by Daniel0108 on 2010-08-24
If it isn't there, download the windows version of teamviewer and start it via WINE :)
It should be in Applications->Wine->C:\->Teamviewer (or something like that) then :)
Hope I helped you,
Yours,
Daniel

---

### Post by gradinaruvasile on 2010-08-24
Should be in the Internet menu.
If its not:
Gnome (defaylt Ubuntu): Run alacarte and see if its there (sometimes icons dont show up right after the program is installed). Untick and then tick the selection checkbox to make it visible.
Xfce or other non-Gnome DEs: here you might have the situation where you cant see certain programs icons. This sucks, there is no menu editor for Xfce for now.

The executable is called teamviewer BTW.

---

### Post by Intrepid Ibex on 2010-08-24
You can just create the icon with alacarte if it didn't get created.

---

### Post by gradinaruvasile on 2010-08-24
> **Daniel0108 said:**
> If it isn't there, download the windows version of teamviewer and start it via WINE :)
It should be in Applications->Wine->C:\->Teamviewer (or something like that) then :)
Hope I helped you,
Yours,
Daniel

Good luck with that. I tried it and you can install it and connect with it to others. But IT DOES NOT accept incoming connections and it depends on your Wines settings making problems very hard to spot.
The Linux version (that is essentially the Windows version + a customized Wine) works. Used it Linux-linux, Linux-Windows, works great.

In Linux you dont have working incoming file transfer (from the other). You can however transfer files to Windows clients.

---

### Post by Daniel0108 on 2010-08-24
> **gradinaruvasile said:**
> Good luck with that. I tried it and you can install it and connect with it to others. But IT DOES NOT accept incoming connections and it depends on your Wines settings making problems very hard to spot.
The Linux version (that is essentially the Windows version + a customized Wine) works. Used it Linux-linux, Linux-Windows, works great.

In Linux you dont have working incoming file transfer (from the other). You can however transfer files to Windows clients.

Oh, sorry :)
I'm new to Ubuntu ;)
Thanks for the info...
Yours,
Daniel

---

### Post by ki4jgt on 2010-08-24
Thanks you guys, I've got a bigger problem altogether though, when I try to use ALT + F2, I can't even get TV to launch from there. What's worse, I've called customer support and they can't help me b/c I don't have a registration number, I don't want to buy the product without trying it out first, but they don't seem to get that. Anyway, I was wondering, does screen resolution matter?

---

### Post by ki4jgt on 2010-08-24
K guys thanks found out what it was. Little piece of advice. Never use a program to speed up your downloads.

---

### Post by jimmers on 2010-08-24
teamviewer5 is available in synaptic, teamviewer came pre-installed with version of Lucid.


Luck

---

### Post by gradinaruvasile on 2010-08-24
> **jimmers said:**
> teamviewer5 is available in synaptic, teamviewer came pre-installed with version of Lucid.


Luck

????

---

### Post by howefield on 2010-08-24
> **jimmers said:**
> teamviewer5 is available in synaptic, teamviewer came pre-installed with version of Lucid.

Where did you get this from ?

It is neither installed with Lucid nor available in Synaptic Package Manager.

The relevant package needs to be downloaded from teamviewer.com

[http://teamviewer.com/download/index.aspx?os=linux](http://teamviewer.com/download/index.aspx?os=linux)

---

### Post by ki4jgt on 2010-08-24
Which brings up another interesting question: Why is everyone still in 8.10 to 9.10 is there something that 10.04 doesn't cover?

---

### Post by howefield on 2010-08-24
> **ki4jgt said:**
> I've downloaded the .deb, after installing, it doesn't show up anywhere in my menus.

For me the menu item shows on install, but a reboot makes it disappear. I tend to add to panel before a reboot. 

To set a launcher manually using System > Preferences > Main Menu the information is as follows.

Name        : Teamviewer
Description : whatever you want
Command     : /opt/teamviewer/teamviewer/5/bin/teamviewer
Comment     : TeamViewer Remote Control Application

The icon is in /opt/teamviewer/teamviewer/5/desktop

---

### Post by jimmers on 2010-08-25
Sorry Guys,
I left out " My" version of Lucid which I got from the Magazine " Ubuntu User ", it comes with lots of pre-installed stuff :-
Picasa, Gimp, Audacity, Google Earth, Google Chrome, Teamviewer, Oracle Virtual box, plus some crud,
at the end of the day it is up to the user what he keeps.

Sorry for the omission.


Jim

---

