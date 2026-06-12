---
title: "Desperately Seeking Software (Windows convert)"
date: 2009-10-23
forum: General Help
---

### Post by arantius on 2009-10-23
I'm using Ubuntu (Hardy) at work now.  I'm very used to Windows, and really missing the features that I'm used to getting from a few key pieces of Windows software.  Can someone suggest programs or settings that will work on Hardy that I can use to get these features?


[LIST]
[*] ClipX [http://www.bluemars.org/clipx/](http://www.bluemars.org/clipx/)
I'm using Klipper now, which works.  But I really miss the ClipX behavior: if I open the history menu with my hotkey, and make a selection, it pastes that _right now_ with no extra keypresses.  Also, the 9 most recent items are accessible by numbers 1-9 with one keypress.
[*] allSnap [http://ivanheckman.com/allsnap/](http://ivanheckman.com/allsnap/)
I love window-edge-snapping to death.  I want it, I want lots of it!  I get OCD over pixel-perfect alignment.  
I'm using Wobbly Windows with snapping inverted to always be on. This only gets me the first feature, and none of the three others. I like wobbly for the visual bell it provides, but will give it up in a heartbeat for these 4 features.
I'm used to allSnap which will do all of:
[LIST]
[*] Snap outer edges (align the edge of one window beside another, or one window to the desktop edge)
[*] Snap inner edges (align the edge of one window atop another, i.e. for making windows the same size)
[*] Snap while resizing (obvious, but not *just* during move)
[*]Snap parallel edges (if two windows have one edge already aligned and one is dragged/resized in the perpendicular direction, edges will snap to be parallel -- this way it's easy to set up windows in a grid arrangement, esp. combined with the previous two to make them the same size)
[/LIST]
[*]Mezer Tools [http://www.fiddlertool.com/mezer/](http://www.fiddlertool.com/mezer/)
One keypress (Super-C) opens on-screen "calipers" that make it easy to measure the size-in-pixels of anything on screen.  Another keypress (Super-S) provides an awesome screenshot-of-a-rectangle tool, with annotations, and saving to a file *or the clipboard*.  A third keypress (Super-P) brings up a dialog with quick screenshot-a-window, color grabber, and hex/decimal conversion.
[/LIST]
 
This might be a tall order.  But I'd seriously appreciate any pointers!

---

### Post by kellemes on 2009-10-23
Try [Parcellite]("http://parcellite.sourceforge.net/") for clipboard management.

[Everything you need]("http://linuxappfinder.com/").

---

### Post by Penguin Guy on 2009-10-23
Some snapping ability can be enabled through the [Compiz Config Settings Manager]("apt:compizconfig-settings-manager"). Once you've installed it you can find the setting in [COLOR="Green"]System -> Preferences -> CompizConfig Settings Manager -> Windows Management -> Snapping Windows[/COLOR].

---

### Post by Jayferd on 2009-10-23
Window snapping is pretty easy with compiz (which you probably have installed).  You might need to install ccsm (Compiz Config Settings Manager):

```
sudo aptitude install simple-ccsm

```

There's all sorts of other cool eye-candy options, too, so play around.

---

### Post by arantius on 2009-10-23
Yes I have, and have configured quite a few things, with ccsm.

Unfortunately, no, its window snapping does not satisfy me.  Both that which wobby windows and that which snapping windows provides gives me only aligning one side of two windows which are side-by-side or above-and-below.  It will not (or if it will please correct me, and show me how!):

* Snap such that adjacent corners (in both directions) are aligned.
* Snap while resizing the window, rather than just moving it.
* Snap to the "inner" edge of a window.

For the latter, I mean I might want to put two different windows in exactly the same spot.  I currently can't do that unless the spot happens to be the corner of the screen, or a corner formed by the screen and another window's outer edge.

As for parcellite, I don't see it in Hardy's repositories.
[http://packages.ubuntu.com/search?keywords=parcellite](http://packages.ubuntu.com/search?keywords=parcellite)
Just Inrepid and newer.

---

### Post by P4man on 2009-10-23
check out the [compiz grid plugin]("http://www.youtube.com/watch?v=Z9hZb7blbVg") and [maximumizer]("http://www.youtube.com/watch?v=-X9bcrJ3TjY")

---

### Post by vinutux on 2009-10-23
What about Glipper ?

---

### Post by arantius on 2009-10-23
None of Glipper, Klipper or Parcellite paste after i select an old item from the list.  None have shortcuts for the most recent items.  Neither Glipper nor Parcellite (as far as I can tell) offer searching/filtering of the list.

And another feature I forgot to mention of ClipX: the previous selection is the default choice, so "Ctrl-Shift-V Enter" pastes the previous clipboard entry.  Handy.

---

