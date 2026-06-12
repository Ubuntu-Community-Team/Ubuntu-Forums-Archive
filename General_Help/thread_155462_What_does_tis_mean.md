---
title: "What does tis mean???"
date: 2006-04-05
forum: General Help
---

### Post by sands on 2006-04-05
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by WakkiTabakki on 2006-04-05
It means that openGL couldn't start (the 3D graphical subsystem). *Possibly *because of some conflict in your /etc/X11/xorg.conf...

You really need to post more information... :-k 
Where did this error appear (which log-file), and was there anymore lines above or below that may be related? 
Did you install och configure anything before you got this error?

Cheers
/N

---

### Post by sands on 2006-04-05
I got this while running a game..
All the 3D screensavers are working well..
Shud i install openGL??

---

### Post by WakkiTabakki on 2006-04-07
Hmm, well... I'm really just guessing here, but...
If you were able to play the game, and suddenly you get this message, I'd say it would suggest that there is a bug in the _game_ rather than in your openGL config...

Questions:
a) Which graphics card have you got?
b) What driver are you using?
c) What is the output from 'glxinfo'?
d) If you run 'glxgears -printfps' what do you get?

Cheers
/N

---

