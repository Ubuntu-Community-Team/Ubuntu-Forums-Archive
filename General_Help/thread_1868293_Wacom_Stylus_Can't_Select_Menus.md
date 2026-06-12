---
title: "Wacom Stylus Can't Select Menus"
date: 2011-10-24
forum: General Help
---

### Post by osarusan on 2011-10-24
Ever since upgrading to Oneiric I've had this problem where my wacom stylus cannot select menu items.

For example, in GIMP, I can draw fine, I can open up menus such as File or Edit, but I cannot select any of the items in the menu. When I click on File nothing happens unless I leave the stylus where it is and click with the mouse.

The same thing happens in the Gimp tabs. If I click on the zoom icon, it won't zoom when I use the stylus. I can change layers with the stylus, I can change tabs, select colors, etc. But I can't select brushes with the dropdown menu or activate the zoom icons (I CAN however use the zoom slider).

The problem is not just in GIMP. It occurs everywhere. I can open menus in any program but I can't select any items within the menus.

Any ideas what this is?

---

### Post by osarusan on 2011-10-24
I seem to have figured out what was causing the problem, but I don't know why...

I have a script that I run to set up the dimensions of my tablet. I tried commenting out each line one by one to see which was causing the bug. It was the line dealing with

xsetwacom set "Wacom Cintiq 21UX stylus" Button 1 1

Not sure why that would cause any problems, but commenting it out seems to have removed the issue.

---

### Post by Favux on 2011-10-24
Now that is interesting osarusan,

That seems to have been affecting people since Natty.  Logging into Compiz without effects fixed it I think unless *xsetwacom set "stylus device name" Button 1 1* was used.  Since it is the driver default I never specify in in my xsetwacom script which is why I was oblivious.

I was thinking at first it might be the gnome-settings-daemon/new Wacom tablet applet in System Settings with GNOME 3.2 in Oneiric, see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)  But the xsetwacom command should override any daemon setting.

So now I'm wondering if some of the changes in BUTTON_ETC (probably by Chris) mainly to accommodate touch changes broke assigning a button with xsetwacom to left click (1).  So starting around xf86-input-wacom-0.10.11?

I think I might ask the list, because I have left handed folks apparently unable to change their mouse button assignments.  I should check if you can still assign a pad button to left click.

So that isn't part of the Gimp history buffer bug.  Are you still seeing the other problems with the windows?

---

### Post by Favux on 2011-10-26
FYI update:

The flying window & Button 1 1 bug was found and fixed today.  Should be submitted and committed shortly, with luck.

---

### Post by osarusan on 2011-10-27
Yeah that was the issue with the jumping windows.

However, the strange line artifacts as reported in that bug still existed.

This Button 1 1 problem only happened upon lifting the stylus away from the screen, and happened reproducably every time. It also is what was responsible for not being able to select menu items.

The other bug happens seemingly randomly. Apparently it is fixed in GIMP 2.7, but as 2.7 is broken on 64 bit Oneiric, I can't use it.

For now, I am using Linux Mint, which is essentially Natty Narwhal with some UI tweaks. I'll try Oneiric again once I hear of this bug getting fixed, or Gimp 2.7 building successfully on Oneiric 64.

---

