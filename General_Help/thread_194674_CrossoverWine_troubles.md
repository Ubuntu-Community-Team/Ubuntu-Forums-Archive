---
title: "Crossover/Wine troubles"
date: 2006-06-11
forum: General Help
---

### Post by kafitz22 on 2006-06-11
I am having trouble with Crossover Office. Every link that was made from within the installation program displays an error similar to this:

Could not launch menu item

Details: Failed to execute child process "/home/user/.cxoffice/win2000/desktopdata/cxmenu/StartMenu/Programs/Microsoft+Office/Microsoft+Office+Word+2003" (Permission denied)

If I add gksu in the launcher, the app closes immediately.

Any ideas as to what could be up? Thanks

---

### Post by taurus on 2006-06-11
[QUOTE=kafitz22]I am having trouble with Crossover Office. Every link that was made from within the installation program displays an error similar to this:

Could not launch menu item

Details: Failed to execute child process "/home/user/.cxoffice/win2000/desktopdata/cxmenu/StartMenu/Programs/Microsoft+Office/Microsoft+Office+Word+2003" (Permission denied)

If I add gksu in the launcher, the app closes immediately.

Any ideas as to what could be up? Thanks[/QUOTE]
Maybe you need to look at the permissions as the error message indicated!!!

---

### Post by kafitz22 on 2006-06-11
sorry, i forgot to add that i changed the permissions to include everybody and still received this message

---

### Post by tebibyte on 2006-06-12
I'm pretty new to linux, but I do have a suggestion. Would using the sudo command help? 
example:
sudo /home/user/.cxoffice/win2000/desktopdata/cxmenu/StartMenu/Programs/Microsoft+Office/Microsoft+Office+Word+2003

---

### Post by kafitz22 on 2006-06-12
yeah, I have tried sudo...the problem i think is that i could not get the script to install normally without errors in permissions so that i installed it using the sudo command. I can not figure out how to install the script without sudo wothout receiving the permission errors.

---

