---
title: "ubuntu arcade"
date: 2009-12-18
forum: General Help
---

### Post by blackmuel on 2009-12-18
hey all! im not really new to ubuntu but i was just woundering if there was a way to do a min-install of ubuntu without gui and then install a psx emulator and have it run automaticly when ubuntu starts...maybe like a server install then apt-get idk...

---

### Post by eric3_14159 on 2010-01-15
That does sound like it would be the right start, a server install and then either apt-get or just download a source tarball or .deb archive from another computer and copy it onto yours. You might not be able to find any psx emulators that write directly to the screen, though, instead of going through the GUI, so you may find that the GUI is necessary. If you want something more lightweight than GNOME, look into xubuntu.

Having a program start up on boot is accomplished by the update-rc.d, which is described in the man pages, if it needs to start before the windows manager has loaded. If the windows manager needs to already be active, then in GNOME you would go to System -> Preferences -> Startup Applications, and I'm there's something similar for Xubuntu but I don't know it off the top of my head.

---

### Post by blackmuel on 2010-01-24
\\:D/thanx for the reply!!! yea i thought it would be somthing like that but that would be sweet with out the gui! :P i havent even tryed anything yet, havent had time, btw the machine it was goin on is a gx270 :D 
 
[HTML] 
Having a program start up on boot is accomplished by the update-rc.d, which is described in the man pages, if it needs to start before the windows manager has loaded.
[/HTML]
 
^^^^ i had no idea you could do this! :P thanx!

---

### Post by eric3_14159 on 2010-01-24
Well, good luck! It's not the easiest thing to do, but it is very rewarding to manage to customize a computer to do exactly what you want to, like that. I hope you succeed!

---

### Post by J V on 2010-01-24
Woohoo, a linux-run playstation arcade, that would be cool :P

---

