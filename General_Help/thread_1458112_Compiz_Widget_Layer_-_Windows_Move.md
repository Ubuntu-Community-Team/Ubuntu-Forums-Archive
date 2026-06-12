---
title: "Compiz Widget Layer - Windows Move"
date: 2010-04-19
forum: General Help
---

### Post by yavoh on 2010-04-19
I have two computers running Ubuntu 9.10, one 64-bit and one 32-bit.

I'm using the Compiz widget layer on both.  Whenever I open the widget layer, whatever windows that I've "pinned" to the widget layer have mysteriously migrated upward ~100 pixels from their previous location.  As a result, I have to keep manually moving them downward.

I've been searching around and I can't find anyone else with this problem.  Do you know how I can go about diagnosing this?

This happens with any class of window I pin to the widget layer (i.e., it's not just one program's windows that exhibit this behavior.)

Thanks in advance!

---

### Post by yavoh on 2010-05-02
bump?

---

### Post by smoluf on 2010-08-30
I also ran into this problem - it turned out that I had selected an animation from the Animations Add-On plugin, but then disabled it. This caused the animation to be listed as N/A, which caused the migratory behavior.

You can actually reproduce if you just set the animation to N/A, independent of any plugins.

---

### Post by yavoh on 2010-09-21
My Animations Add-On plugin is enabled :\

---

### Post by StephGbzh on 2010-10-26
Hi,

On my freshly upgraded Ubuntu 10.10, I had only the "Animations" plugin enabled, and there was indeed the "Focus Animation" set to Focus Effect=N/A.
But even after setting it to a real effect (Fade), I still get this annoying behavior : the window is fleeing 100 pixels to the sky and beyond each time I activate the Compiz widget layer ! :(

This was found on LaunchPad : [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/574585](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/574585) but nobody seems to care about it.

Any news or idea is welcome!

---

### Post by smoluf on 2010-11-08
It seems that my old N/A trick no longer works, I am also experiencing the window fleeing problem with 10.10. A temporary workaround I've found is to disable window decoration on widget layer windows.

---

### Post by JustinR on 2010-11-08
Does disabling 'Snapping Windows' fix the problem?

---

### Post by StephGbzh on 2010-11-11
Disabling 'Snapping Windows' does not help.
As I tried to re-enable it, CCSM told me that it conflicts with 'Wobbly Windows' so I disabled this plugin too, but to no avail.

Disabling window decoration does work indeed but I only hope it will help developers find a solution, as I want to be able to move my window ! :)

Thanks for your suggestions anyway.

---

### Post by mcduck on 2010-11-11
If disabling window decorations solves your problem, perhaps you could try excluding everything you use with Widget Layer in the Window Decoration-plugin.

That way you'd still have decorations for everything else.

Also, you don't need the decorations to move windows. Hold down the Alt key and you can move a window from any point, not just the titlebar. (Alt+left button moves, Alt+middle button resizes). This should allow you to move your widgets even if you disable their decorations.

---

### Post by StephGbzh on 2010-11-11
Yes, excluding only the windows I put in Widget Layer is what I already did : I replaced 'any' with '!(class=Terminator)' in the 'Window Decoration' plugin.

What I did not know is that decoration is not needed to move windows. Thanks for the shortcuts, all this is now usable enough for my liking!

---

