---
title: "Accidentally closed panel, how to restart"
date: 2011-01-11
forum: General Help
---

### Post by sandyp on 2011-01-11
When I installed Ubuntu, I had two panels.  The first one has application, places, system, shortcuts and time.

The second one had all of my icons and when I minimized an app, I could access it off of the second panel.

I have closed this second panel and don't know how to restart it.  Now when I minimize an app (eg browser), I have to press alt-tab and toggle through the open apps until I get to the one I need.

Could someone advise how to get this panel back.

Thank you

---

### Post by WorMzy on 2011-01-11
You have two options.

1) Manually add another panel and re-add all the applets which you need. Do this if you have made significant changes to your top panel which you would like to keep.

To do this, right-click on an empty part of your top panel and choose "New Panel". This should add a new, empty panel to the bottom of the screen, but it may add it to the right or left sides instead. If this happens, right-click on the new panel and choose "Properties", in the window that pops-up, change the Orientation value to "Bottom", and close.

To add items to the new panel, right-click it and choose "Add to Panel". All the applets that you had before will be in the list, it's simply a matter of finding them and dragging them onto the panel where you want them to be.

Alternatively...

2) Revert gnome-panel to it's default state, losing all the changes you've made to it.

To do this, simply run the following commands in a terminal (Applications -> Accessories -> Terminal):

```
gconftool-2 --shutdown
rm -r ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by sandyp on 2011-01-11
Thank you, I've recreated the panel.  I thought maybe there might have been to toggle it back on with a keystroke if I had accidentally just hidden it.

---

