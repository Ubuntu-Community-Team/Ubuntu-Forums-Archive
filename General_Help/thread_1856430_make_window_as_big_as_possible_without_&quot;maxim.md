---
title: "make window as big as possible without &quot;maximizing&quot; it?"
date: 2011-10-08
forum: General Help
---

### Post by CryptKeeper777 on 2011-10-08
I want to be able to maximize the size of a window without really maximizing it, i.e. without the window title bar being integrated into the unity top panel. Though the standard maximization state is fine for windows like the browser, it sucks if I have e.g. several maximized PDF windows (document viewer) because I can't really switch between them using the window overview feature (the equivalent to Mac Éxposé) with the pointer keys (that is, without using the mouse).

I don't think this is possible "out of the box". But I think there should be a way to make a custom command or script which resizes the current window to maximum size vertically and horizontally and to define a shortcut then (the latter could easily be achieved using Compiz). I just don't have ANY idea how to achieve this. 

Any suggestions?

---

### Post by WasMeHere on 2011-10-08
Try alt + TAB, at least in 10.04 LTS it switches between different maximized windows (I tried a minute ago).

Have fun
Olle

---

### Post by CryptKeeper777 on 2011-10-08
I know there are different ways to switch between windows and that that also works with maximized windows. The tab switching is also perfect to switch to and fro between two windows. But I specifically mean switching between windows with the "Éxposé" feature and the arrow keys. With normal windows that works fine because the currently active window has a blue top bar and the others a gray one (with the theme I use), but since the maximized windows don't have a top bar anymore, that doesn't work.

That's why I'm looking for a fast way to make normal windows as big as possible without actually maximizing them.

---

### Post by WasMeHere on 2011-10-08
Well, some programs have the *-geometry* option, so that you can call them with a window-size to fit your resolution, or even use *xrandr* to probe for the resolution and make them 'full-size'. But some programs lack that option.

Other programs save the window position and size from the previous invocation. That would also work for you. But I don't know a general way to accomplish what you want. Maybe someone else who reads this thread knows :-)

---

### Post by CatKiller on 2011-10-08
You could just turn off Unity's weird handling of maximised windows. Use CCSM; there are a whole bunch of window management options in there.

---

### Post by CryptKeeper777 on 2011-10-08
> **CatKiller said:**
> You could just turn off Unity's weird handling of maximised windows. Use CCSM; there are a whole bunch of window management options in there.
That might be an option. Does anybody know where in Compiz this option is? I just took a look, but there are so many options that I could search myself to death...

---

### Post by CatKiller on 2011-10-08
I'm not at my computer, so I can't check, and I must admit to turning Unity off almost immediately, but I believe that feature is called maximumise.

CCSM isn't really a shining example of interface design.

---

