---
title: "CSS with Wine (I know it's been posted 1000 times, im sorry)"
date: 2009-07-25
forum: General Help
---

### Post by baz8771 on 2009-07-25
Hey guys, I have CSS installed in ubuntu 9.04 already, but when I get into the game and select a server, the game crashes.  I can get into the server and I can see the screen where you have to press "ok" to accept server rules and what not, but then the game freezes right there and crashes to desktop.  I can provide the debug details or whatever, if somebody can instruct me how to do that.  I suspect that it has something to do with directx  but I'm not sure.  Any help is appreciated, thanks :)

---

### Post by synapsys on 2009-07-25
You need to tell your wine installation to use directx. Open up a terminal and type 
```
winecfg
```

and check your settings.

---

### Post by baz8771 on 2009-07-25
> **synapsys said:**
> You need to tell your wine installation to use directx. Open up a terminal and type 
```
winecfg
```

and check your settings.


I did that and I have "default settings" and "dxsetup.exe" in the "applications" tab... is that right?

---

### Post by diggedy on 2009-07-25
open steam > settings> in-game and untick the "enable steam community in-game" box

this should fix your problem. You might get periodic crashes when youve been playing for a while, take a look here [http://forum.winehq.org/viewtopic.php?p=25107#25107](http://forum.winehq.org/viewtopic.php?p=25107#25107) if you do

---

### Post by baz8771 on 2009-07-25
> **diggedy said:**
> open steam > settings> in-game and untick the "enable steam community in-game" box

this should fix your problem. You might get periodic crashes when youve been playing for a while, take a look here [http://forum.winehq.org/viewtopic.php?p=25107#25107](http://forum.winehq.org/viewtopic.php?p=25107#25107) if you do


That made some progress.  Now instead of crashing as soon as i get to the "OK" screen, I see like 5 or 6 frames of gameplay in the background and then it freezes and crashes to desktop

---

### Post by baz8771 on 2009-07-25
Anybody?  Any suggestions at all?

---

### Post by diggedy on 2009-07-26
have you tried that link regarding pulse audio?

---

### Post by diggedy on 2009-07-26
also read this

[http://ubuntuforums.org/showthread.php?t=1222912](http://ubuntuforums.org/showthread.php?t=1222912)

create that same launcher (replace "name" with your ubuntu user name) and run steam from there. see if that helps as that should suspend the pulse audio

---

