---
title: "Workspace Switcher missing important functionality"
date: 2010-03-20
forum: General Help
---

### Post by ibob_gr on 2010-03-20
I just installed a fresh copy of 9.10. My problem is the way Workspace Switcher 2.28.0 (the default of the installation) with compiz running (I haven't tried without compiz)

Old behaviour: (9.04 and 8.10)
a) rolling the mouse wheel over a workspace of the workspace switcher means: move to the next or previous workspace
b) click on a the representation of a window (a little square) on the the workspace switcher and then drag it to another workspace means: move window to other workspace

In 9.10 the workspace switcher does work (the number of workspace can be configured, Ctl-Alt-left & right arrow, Ctlr-Shiht-Alt-right&left arrow) but the functionality described in a and b is missing.

Moreover, I can't find where I could configure the behaviour of workspace switcher.

So, I would like to ask if you know how to:
1) configure in general the workspace switcher
2) enable this specific functionality

A similar thread exists in [http://ubuntuforums.org/showthread.php?p=8775791](http://ubuntuforums.org/showthread.php?p=8775791) but the solution is on a different matter. Apart ffrom that I could find any other references.

[edit]: fix error in a)

---

### Post by darolu on 2010-03-20
The mouse wheel option is at "Desktop Switcher" (or viewport switcher) option in CCSM, assign the move to next/previous option to Button 4 and 5 of your mouse.
I don't use the little square you mention, but I suppose you can configure it with CCSM as well.

If you don't have CCSM (compiz configuration setting manager) install it from Synaptic or from a terminal with:
```
$ sudo apt-get install compizconfig-settings-manager
```

---

### Post by ibob_gr on 2010-03-20
Darolu thanks for your prompt reply.

The problem is that the settings you describe, have to do with the interaction with Compiz in the area of the whole screen. So, the move next/prev workspace works only when I use the mouse wheel on an empty desktop surface. See the 1st attachment, the area marked with green.

The behaviour (a and b of post #1) of the "Workspace Switcher" was working on the area of the workspace switcher itself, See the 2nd attachment, the area marked with green (bottom right corner).

---

### Post by ibob_gr on 2010-03-21
I also noticed that when I hover the mouse over a window representation of a window (a little square) over the workspace switcher, I get a tooltip:

```
Click to start dragging "window_title" 
```

See attachment, bottom left corner. Of course this doesn't work, as I mentioned in post #1.

---

### Post by chillipepper on 2010-04-27
I also am looking for a way to make the workspace switcher work.  I want item b) in the first post to work.  I want to be able to switch an application between workspaces by dragging it from one workspace to another in the workspace switcher.  When I used gnome in years past, this worked.

c) I also would like to be able to assign which workspace any given application will open in.  I should be able to click three apps, and have them open in their assigned workspaces, not all on top of each other.

I am trying to get Gnome configured so I can switch from KDE, but these things are pretty much show-stoppers.  I have found there is a convoluted workaround for c), but it requires Compiz which I think precludes any solution for a).

---

