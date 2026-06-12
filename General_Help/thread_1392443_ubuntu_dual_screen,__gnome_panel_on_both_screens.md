---
title: "ubuntu dual screen,  gnome panel on both screens"
date: 2010-01-28
forum: General Help
---

### Post by readycarpenter on 2010-01-28
I reinstalled and forgot how I added a panel to my second screen, cause when you add a panel you choose left right top or bottom, but no option for second screen...

finally I added a new panel, then right click on the new panel> properties, then unchecked "expand" then was able to move the new panel to second monitor, then set to whatever side and recheck "expand" then it sticks to the second screen, then add to panel, and select window list, then all new windows will be shown on the appropriate panel/screen

hope this helps someone..

---

### Post by Paddy Landau on 2010-05-23
Thank you, it helped me!

---

### Post by m4lte on 2010-09-15
Is there actually a way to extend a panel to span across two monitors.
Or is there a way to see the panel duplicated on the second monitor?
Or is there a way to use two monitors as two workspaces, so that the window list in the panel only shows the windows from the monitor (workspace) that is currently active?

---

### Post by Paddy Landau on 2010-09-15
> **m4lte said:**
> ... is there a way to use two monitors as two workspaces, so that the window list in the panel only shows the windows from the monitor (workspace) that is currently active?
I'm not sure. Unfortunately, one of my screens no longer works so I can't test this, but here's how I would try:

[LIST=1]
[*]Add a new panel to the second screen and add *Window List* to it.
[*]Go  to your Compiz settings (System > Preferences > Compiz Config  Settings Manager).
[*]Desktop > Desktop Wall > Viewport Switching  > Multi-monitor behavior > Switch All.
[/LIST]
Try that and let me know whether it works.

BTW, you need visual effects enabled (System > Preferences > Appearance > Visual Effects > *either* Normal *or* Extra).

---

### Post by RCCola on 2010-11-08
> **Paddy Landau said:**
> I'm not sure. Unfortunately, one of my screens no longer works so I can't test this, but here's how I would try:

[LIST=1]
[*]Add a new panel to the second screen and add *Window List* to it.
[*]Go  to your Compiz settings (System > Preferences > Compiz Config  Settings Manager).
[*]Desktop > Desktop Wall > Viewport Switching  > Multi-monitor behavior > Switch All.
[/LIST]
Try that and let me know whether it works.

BTW, you need visual effects enabled (System > Preferences > Appearance > Visual Effects > *either* Normal *or* Extra).

I added a new panel to my second screen per the OP, added a window list, and then switched workspaces (to refresh the panel). The window list in the panel in my second window picked up only the windows on that screen.

Didn't need to mess with Compiz.

Initially, the new panel and my old panel were a bit bugged out - the window list didn't show the appropriate windows, but switching to another workspace then back redrew the panels and all looks fine now.

---

