---
title: "Panels gone"
date: 2009-10-31
forum: General Help
---

### Post by ThorgrimA on 2009-10-31
Today when I logged into Ubuntu 9.10, I noticed that the menu panels were all gone. I searched for a solution on here, and found something smiler. I used Ctrl Alt F1 to get into the terminal, and tried to run system monitor, but it returned an error. I'm new to linux so I'm still trying to work out the commands and processes.

---

### Post by StolenPie on 2009-11-01
I recently had this problem.
You can do a temporary solution by pressing right click > Create Launcher
Type in Gnome Panels in name, and gnome-panels in command.

This will give you access to the menu's again.

You might find that your window borders are gone once you start navigating around the computer.
You can make a launcher for Metactiy (the windows manager) in a similar way: right click > Create Launcher, execpt this time type metacity in the space for command.

For me, I found the source of the problem to be that Gnome Panels and Metacity were missing from the Start-up Applications. If you go System>Preferences>Startup Applications, then you can check the list to see if they are there. If they aren't, click Add. Then add the programs the same way you made the launchers.

Hope this helps.

---

### Post by ThorgrimA on 2009-11-01
Thanks for that, although I didn't get the chance to test it because I decided to format and reinstall 9.04.

---

### Post by dbyjazz on 2009-11-01
ThorgrimA, please mark as 'solved'

---

