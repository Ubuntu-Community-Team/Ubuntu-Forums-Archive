---
title: "Belkin F5D8053 on Ubuntu?"
date: 2009-10-30
forum: General Help
---

### Post by mebecj on 2009-10-30
I've been googling this for a while now. I'm really new to Linux, I only installed it last night. After I got it installed, I found out my adapter doesn't work.

I'm running Jaunty Jackalope, and I can't seem to connect to a wireless network using my Belkin F5D8053 N USB Adapter. I've tried two methods already, and neither is getting me connected.

I understand the basics of Linux, such as installing packages, and I already have WINE and ndiswrapper installed. I just need a way to get this working so I can finally cut windows out of the picture.

---

### Post by marshag63 on 2009-10-30
On the Windows install disk for your adapter, in the windows XP driver section you need to find:  3 files from that disk: RT2870,sys, RT2870.inf and RT2870.cat and copy them to your home folder (i.e. /home/YOURUSERNAME/)

Now start up your windows wireless driver app (Administration > Windows Wireless Drivers), enter your password and then "add new driver" which is in your home folder:  /home/YOURUSERNAME/RT2870.inf.

Hope this helps :)

MarshaG.

---

### Post by mebecj on 2009-10-30
> **marshag63 said:**
> On the Windows install disk for your adapter, in the windows XP driver section you need to find:  3 files from that disk: RT2870,sys, RT2870.inf and RT2870.cat and copy them to your home folder (i.e. /home/YOURUSERNAME/)

Now start up your windows wireless driver app (Administration > Windows Wireless Drivers), enter your password and then "add new driver" which is in your home folder:  /home/YOURUSERNAME/RT2870.inf.

Hope this helps :)

MarshaG.

I don't seem to have a windows wireless driver app...

EDIT: Whoops, probably should have put this in networking :P

---

### Post by marshag63 on 2009-10-30
Are you running regular Ubuntu 9.04 or some other version?  It should be under the "Administration" menu - down toward the very bottom.

MarshaG.

---

### Post by mebecj on 2009-10-30
I'd assumed it was just Ubuntu... I used the Windows installer, is that any different of a version?

---

### Post by marshag63 on 2009-10-30
Is this a "wubi" install?

MarshaG.

---

### Post by mebecj on 2009-10-30
That's the one. Name escaped me for a moment, but that's it.

---

### Post by marshag63 on 2009-10-31
I've never used "wubi" - I assume you still need to install the driver through Ubuntu for Ubuntu to access wireless.

From within Ubuntu, put the windows driver CD for your adapter in your CD-rom drive and find the windows XP driver folder, copy the 3 files mentioned above into your "home" folder in Ubuntu as above.  Then, through the menu, choose "administrative" and scroll down the list until you find the "Windows Wireless Driver" entry.  When you start it up, you need to enter your password, then tell it you want to add a new driver, which you should have already copied into your Ubuntu Home partition (/home/YOURUSERNAME?)

Please post back and let us know what you find.

MarshaG.

---

### Post by mebecj on 2009-10-31
> **marshag63 said:**
> I've never used "wubi" - I assume you still need to install the driver through Ubuntu for Ubuntu to access wireless.

From within Ubuntu, put the windows driver CD for your adapter in your CD-rom drive and find the windows XP driver folder, copy the 3 files mentioned above into your "home" folder in Ubuntu as above.  Then, through the menu, choose "administrative" and scroll down the list until you find the "Windows Wireless Driver" entry.  When you start it up, you need to enter your password, then tell it you want to add a new driver, which you should have already copied into your Ubuntu Home partition (/home/YOURUSERNAME?)

Please post back and let us know what you find.

MarshaG.

I've already told you that I don't have the Windows Wireless Driver thing. I did copy the drivers over to home though.

---

### Post by marshag63 on 2009-10-31
Perhaps stopping by the IRC channel #ubuntu (irc.freenode.com) can shed some light on this for you.  Meanwhile, I will scan the wiki regarding wubi (that sounds funny LOL).

BTW, do you have any kind of networking icon show-up?  If so try right clicking and choosing "edit configurations."

MarshaG.

---

### Post by mebecj on 2009-10-31
I don't think there's anything different between a normal and wubi install. It's still dual-boot.

EDIT: Nevermind, one major difference is that there's no partition in the harddrive.

---

### Post by marshag63 on 2009-10-31
Sorry, I edited a previous post and didn't see your last one.  

Do you have any kind of networking icon on your menu bar (either two computers or if wireless - a stairstep of bars).

MarshaG.

---

### Post by mebecj on 2009-10-31
> **marshag63 said:**
> Sorry, I edited a previous post and didn't see your last one.  

Do you have any kind of networking icon on your menu bar (either two computers or if wireless - a stairstep of bars).

MarshaG.

That much I have.

EDIT: But that doesn't let me do anything about the drivers.

---

### Post by marshag63 on 2009-10-31
Which do you have - two computers (which is ethernet connection) or the stairstep bars?

btw, look under your "System" menu (in ubuntu) for networking or wireless driver.

MarshaG.

---

### Post by mebecj on 2009-10-31
> **marshag63 said:**
> Which do you have - two computers (which is ethernet connection) or the stairstep bars?

btw, look under your "System" menu (in ubuntu) for networking or wireless driver.

MarshaG.

It's technically neither, it's just where one of those would be. I'm online on XP right now, There's no possible way I can do wired.

EDIT: And I know it would be under system. It's not there. I know where you're telling me to look, it is not there.

---

### Post by marshag63 on 2009-10-31
ummm..... yeah......I think you have all the pieces you need - ndiswrapper, ndiscgtk and the three files discussed previously.  Once you find how to access Ubuntu's networking/wireless setup and add your *.inf file to th wireless drivers, you should be good to go.

BTW, welcome to the world of Linux!

Good luck!

MarshaG.

---

### Post by mebecj on 2009-10-31
> **marshag63 said:**
> ummm..... yeah......I think you have all the pieces you need - ndiswrapper, ndiscgtk and the three files discussed previously.  Once you find how to access Ubuntu's networking/wireless setup and add your *.inf file to th wireless drivers, you should be good to go.

BTW, welcome to the world of Linux!

Good luck!

MarshaG.

I didn't have ndisgtk installed, and even though it made the menu item show up, it's just a frontend for ndiswrapper, and I'd already used that to install the drivers. It's still not working.

---

### Post by mebecj on 2009-10-31
Bump, I'd really like to get this fixed.

---

### Post by marshag63 on 2009-10-31
Correction:  I saw a video - try System > Preferences > Network Connections.

I'm told in Jaunty you navigate:  System > Administration > Hardware Drivers.  The wireless driver installer application is GUI - I'm pretty sure you need ndisgtk to use the GUI wireless driver installer app.  I've installed wifi driver via CLI (love CLI), but I prefer the GUI for installed wifi drivers.

Again, good luck  :)

MarshaG.

---

