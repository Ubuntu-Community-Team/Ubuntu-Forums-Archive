---
title: "Erratic images in top panel.."
date: 2011-08-17
forum: General Help
---

### Post by oxf on 2011-08-17
Does anyone else experience this phenomena? It only happens on one of  my PC's, my Compaq Presario M2000 laptop.

The icons for various applications in the top panel load eratically on boot up. E.G sometimes the wireless icon doesen't appear , sometimes it loads twice. Sometimes  the Sound Preferences (the speaker icon) is missing, Evolution Mail etc etc. Even the shutdown icon occasionally is gone. It sees limited to the ones on the right side  and doesn't seem to affect ones such as Firefox that I've dragged up there myself. It doesen't happen every time, I'd say about 20% of boot ups this happens.

Katya

---

### Post by Elfy on 2011-08-17
Have you tried locking the panel to see if that does it. There's a setting in gconf-editor - not running gnome at the moment so I can't check - I think it's either in the apps > nautilus or apps >metacity keys, possibly apps >gnome-panel

Edit - maybe apps&#8221; > &#8220;panel&#8221; > &#8220;global

I took the liberty of changing the thread title to erratic from erotic.

---

### Post by frankbooth on 2011-08-17
> **forestpiskie said:**
> I took the liberty of changing the thread title to erratic from erotic.

:lolflag:

---

### Post by oxf on 2011-08-17
> **forestpiskie said:**
> Have you tried locking the panel to see if that does it. There's a setting in gconf-editor - not running gnome at the moment so I can't check - I think it's either in the apps > nautilus or apps >metacity keys, possibly apps >gnome-panel

Edit - maybe apps” > “panel” > “global

I took the liberty of changing the thread title to erratic from erotic.

Oh I guess that's what I meant LOL!!!

Uhm yes they are all locked to panel so it's not that.

---

### Post by Elfy on 2011-08-17
Is the panel globally locked? gconf-editor somewhere.

Of course if this is in Unity then I'll bow out as I have no idea at all with that ...

---

### Post by oxf on 2011-08-17
Heres an example of the wireless icon right now.

---

### Post by oxf on 2011-08-17
> **forestpiskie said:**
> Is the panel globally locked? gconf-editor somewhere.

Of course if this is in Unity then I'll bow out as I have no idea at all with that ...

I don't quite understand what you mean by that?
I just right click the icons and lock

---

### Post by Elfy on 2011-08-17
[s]Alt+F2 and run gconf-editor

Navigate to apps > panel

then I think there's an option to globally lock the panel.

Though as I said it might be in metacity or nautilus. I can't check as I moved to xubuntu. 

I have also in the time I've been here seen all manner of odd things happen when / starts to be full.[/s]

Edit - hang-on - I see what you mean now - looks like a ghost. 

I've had that happen once - but that was with awn. 

I'll have a think - but it might be worth moving this to Desktop Environments and tweaking the title somewhat. 
Tell me if you want me to do that

---

### Post by Elfy on 2011-08-17
If you try a different theme does it go away?

---

### Post by scorp123 on 2011-08-17
> **oxf said:**
> Does anyone else experience this phenomena? Yes, I do. It happens here and there.

What I did:

I made a custom application launcher icon that executes the following command:
```
killall -1 gnome-panel
``` The erratic GNOME panels get killed and new ones get launched, thus correcting the problem. No idea what is causing this. But above command is a quick and easy workaround. Whenever those "ghosts" show up ... one click ... pooof! gone. New panels instantly appear and the problem is gone until it appears again ... maybe. Or maybe not. It's not really predictable.

---

### Post by oxf on 2011-08-18
> **forestpiskie said:**
> If you try a different theme does it go away?


I'll have to test this for a little while Since it doesn't happen every time I can't give an immediate answer. But my memory is that it did happen with other themes. Now I think about it not just with Maverick either, I had it on Karmic too. To clarify it's not only "ghost" icons but mising ones too.


By all means move this thread to Desktop Environemnts if you think thats better. New Title? sure! uhm? "Ghost/missing icons in top panel" ? If you have a better idea go for it! 

Thanks
Katya

---

### Post by oxf on 2011-08-22
Any further ideas anyone?

---

