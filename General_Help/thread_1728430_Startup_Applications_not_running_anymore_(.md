---
title: "Startup Applications not running anymore :("
date: 2011-04-13
forum: General Help
---

### Post by swatto on 2011-04-13
Hey all,

Im not sure why they aren't working - but my startup applications are not running at boot.  They run fine from terminal.

I have a startup application for Xchat and the command is just xchat (which works fine from terminal) but it isn't loading at? - please help (I have checked and im not running in safe mode or anything like that - just the standard ubuntu desktop).

*Unrelated Question:*

Is there a 'global' i.p address I can use to represent all devices on my LAN - so I can mass whitelist in firestarter?

Thanks for any help on this

---

### Post by lithopsian on 2011-04-13
What desktop are you using?  I don't even remember what Jaunty came with.  Metacity?

---

### Post by poodoopealeoaph on 2011-04-13
system>preferences>startup applications. go there and see if everything is still set up to auto load and if there are things missing, simply add them to the list and it should work.

---

### Post by swatto on 2011-04-13
Hello Both,

Sorry forgot to update my profile.  Im using Ubuntu 10.10.

When I add applications in Preferences > Startup Applications it does not run on startup.  I have tried dragging the application from the applications menu to get the absolute path in the command box but the application still will not load.

What is interesting is that when I create a symlink to the application in ~/.config/autostart/ using the CLI the application loads? but using this method I cannot add startup arguments to the application (for example, i would like xchat to start minmized to systray using --minize=2)

---

### Post by swatto on 2011-04-14
Bump - anyone know why creating a symlink manually to autorun works but it won't work when configuring through the GUI > Startup Applications?

Is there a way I can reinstall the startup applications part of ubuntu or clean it out and start fresh on it? (reset to default)

---

### Post by swatto on 2011-04-15
Ive fixed this now - turns out I had a corrupt profile so had to make a new user/group.  My question now is, is there something that can backup my current profile incase this happens again or check it for errors?

Thanks for any help ):P

---

