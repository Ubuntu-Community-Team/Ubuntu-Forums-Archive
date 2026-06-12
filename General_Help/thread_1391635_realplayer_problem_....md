---
title: "realplayer problem ..."
date: 2010-01-27
forum: General Help
---

### Post by pirlo89 on 2010-01-27
I have installed real player and when i go to applications>>sound and video>>realplayer 11   ,  nothing happens . So i went to the folder where its installed" /usr/share/realplay " and clicked on the realplayer icon and this what happens :

[COLOR=Red]There was an error launching the application.
Details: Failed to execute child process "realplay" (Permission denied)[/COLOR]

and BTW, i have tried going to system>>preferences>>main menu and put sudo in front of the command for real player , but it didnt solve it.

---

### Post by raktarok on 2010-01-27
Since you are dealing with a graphical app here, try putting gksudo, not sudo.

Or from a terminal, launch the realplayer(I don't know the command to start realplayer, but the launcher entry in main menu should have it) Launch the player with sudo and without it. See what happens and post any errors that you see.

---

### Post by pirlo89 on 2010-01-27
problem solved. i had to reinstall and use the default directory offered by real player. i guess the program didn't have permission to run in the share folder. 

but thanks for the help though, i learned from you the gksudo command.;)

---

