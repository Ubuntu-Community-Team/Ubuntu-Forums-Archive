---
title: "Big black box around Cairo-dock"
date: 2009-12-27
forum: General Help
---

### Post by Admiral Yi on 2009-12-27
Hello,
I have recently installed cairo-dock (the latest version from the cairo-dock repository) on my laptop. Technically I'm running Crunchbang Linux Jaunty, but this is built off Ubuntu, so I'm posting this here (they don't seem to have a help forum over at Crunchbang). 

I have tried running it with OpenGL on and off, but whatever I do there is always this big black box surrounding the dock that goes on top of my other windows and makes it impossible to use. I have also tried enabling compositioning, but this doesn't seem to do a lot either. 

The laptop is quite old and has only 512mb of RAM (which I why I am running the more lightweight Crunchbang rather then Ubuntu). Could a lack of RAM be causing the problem? I doubt it, as the desktop doesn't seem to slow down or lag, but I'm not sure. 

Any help would be appreciated.

---

### Post by Shpongle on 2009-12-27
I used to run cairo , and it worked on crunchbang fine , you have to have compositing turned on and i had to run it without opengl , i think i ran it with the -c parameter to use cairo instead , also i had to edit the autostart.rc file (i think thats what its called) to enable compositing on startup , hope this helps

---

### Post by Shpongle on 2009-12-27
you could also try awn, im using it a good while now and i find its less buggy than cairo was , although i havnt tried cairo on karmic yet

---

### Post by Admiral Yi on 2009-12-27
Ah, thanks! I had only tried it with both compositioning and opengl on, not with opengl off. Is there a way to have compositioning on but not make the windows fade in and fade out?

---

