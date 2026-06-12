---
title: "Ubuntu Unity Panel Won't Auto-Hide"
date: 2011-08-08
forum: General Help
---

### Post by notfed on 2011-08-08
Hi,

I've recently installed Ubuntu 11.04 on a friend's laptop, and installed WINE so he could play Warcraft III.  The game worked without any real problems, which I'm happy about.  

One problem is that the game runs full screen and he can't alt-tab out of the game; if anyone knows how to fix that, it would help.  Super+D doesn't do anything, either.  Not sure if this can be fixed with  a Wine setting.  Also, after just pressing Super (which happens on accident sometimes), which brings up the unity dash, and then going back into the game, sometimes the game loses keyboard input and super has to be pressed a few more times until it gets control back.  Not sure what's up with that.

Another issue, and the reason I posted to this forum, is that the top panel is still visible when the game is running. In an older version of Ubuntu, I'd have right clicked on it, clicked Properties, then checked Auto-hide.  I can't even right click now.  I went into gconf-editor, searched for the top panel and manually selected auto-hide.  The panel STILL does not auto-hide.  Why is this?

Thanks,
Jay

---

### Post by uRock on 2011-08-08
Bump for move to *General Help*.

---

### Post by marin123 on 2011-08-08
you can try alt+f9, thats minimize, but i doubt it will work.

when you alt-tab the game, try clicking on the game with your mouse. i think thats why you lose keyboard, because its not in front.

you can hide panel if you go to winecfg (Graphics tab, check Emulate a virtual desktop) and make app start with virtual desktop of your screen size (ie. for my laptop 1366x768 px), that would overlay your whole desktop and you would lose the upper panel.

---

### Post by Frogs Hair on 2011-08-08
I'm not sure about that game , but F11 toggles in and out of full screen for other applications . You can try Esc as well .

---

