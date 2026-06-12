---
title: "no printer config in System-Administration"
date: 2011-11-09
forum: General Help
---

### Post by georgec32 on 2011-11-09
I have Ubuntu 10.10 on an HP laptop and just got a new wireless printer that I wanted to install .. I went to System-Administration and didn't see the menu entry for 'printers' .. I checked the 'main menu' to see if I had somehow disabled it, but I can't find it anywhere.  I did a few google searches but they all are just info on how to install a printer, with the assumption that it's listed in the menu.  

Can someone tell me how to get this to appear back in the menu?  BTW, I checked my user privilege and am enabled for configuring printers, so it -should- show up I think.

thanks for any help/advice/pointers/politelysuppressedlaughter

george c

---

### Post by bluexrider on 2011-11-09
Don't know where it went but you can get there by doing this:

Alt+F2 type "system-config-printer"

---

### Post by georgec32 on 2011-11-09
> **bluexrider said:**
> Don't know where it went but you can get there by doing this:

Alt+F2 type "system-config-printer"


Thanks for the quick reply & the help :)   I tried that and I get the message: *Could not open location 'file:///home/george/system-config-printer'*.  I'm totally confused .. I have to admit that I use Ubuntu as a toy, loading up apps just to see what they do, running almost everything in sight, etc, so I can easily believe that I screwed this up somehow, but I can't understand why no printer config .. and more importantly than that, I can't figure out how to get it back .. 

george c

---

### Post by bluexrider on 2011-11-10
This may help

[http://www.liberiangeek.net/2010/10/add-network-printer-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/add-network-printer-ubuntu-10-0410-10-maverick-meerkat/)

---

### Post by 3rdalbum on 2011-11-10
Since you're using an old Ubuntu, you might need to install a driver for the new printer, or update HPLIP if it's an HP printer.

---

### Post by bluexrider on 2011-11-10
> **3rdalbum said:**
> Since you're using an old Ubuntu, you might need to install a driver for the new printer, or update HPLIP if it's an HP printer.

How is he going to install a driver when he can't even find his printer config?

---

### Post by georgec32 on 2011-11-10
> **bluexrider said:**
> How is he going to install a driver when he can't even find his printer config?

yep .. that's exactly the problem.  I may end up bailing out & just re-installing Ubuntu.  BTW, version 11.x has such a different look & feel that I wanted to stick w/ 10.10 for a while ... by now, there's probably an update that allows the older look & feel but has the new advantages of Ubuntu 11  :)

BTW#2, I did make sure my user ID was set up to enable configuring printers .. no problem there .. it's just not showing up.

Once again, thanks for all the help & suggestions.  It is very much appreciated!

george c

---

### Post by bluexrider on 2011-11-11
Here's a last ditch effort.

Open Synaptic and in the search window type 
system-config-printer

Look for and reinstall this:

system-config-printer-gnome

system-config-printer-common 

system-config-printer-udev

---

### Post by georgec32 on 2011-11-12
> **bluexrider said:**
> Here's a last ditch effort.

Open Synaptic and in the search window type 
system-config-printer

Look for and reinstall this:

system-config-printer-gnome

system-config-printer-common 

system-config-printer-udev



Thanks!  That worked great :)  Many thanks to all who offered advice/help!  

george c

---

