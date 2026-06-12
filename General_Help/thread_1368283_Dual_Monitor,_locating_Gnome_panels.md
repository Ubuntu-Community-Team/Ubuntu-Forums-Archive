---
title: "Dual Monitor, locating Gnome panels"
date: 2009-12-30
forum: General Help
---

### Post by teachop on 2009-12-30
In my dual monitor setup, the gnome panels are on the external monitor when it is present, else they are on the laptop screen.  I can relocate them, but they will always go back to this arrangement.  Is there a way to have the panels always be on the laptop screen, regardless of having / not having the external monitor connected?  Thanks.

---

### Post by scouser73 on 2009-12-30
I think it's possible by making the laptop screen be the primary monitor.

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by Jenkins1 on 2009-12-30
Interesting I find mine always stay on the laptop even if I have an external display connected 

```
gconftool-2 \
        --set "/apps/panel/toplevels/bottom_panel_screen0/monitor" \
        --type integer "0"
        
   gconftool-2 \
        --set "/apps/panel/toplevels/top_panel_screen0/monitor" \
        --type integer "0"
```

That should move your top and bottom panel to your laptop display if it will stay there or not I do not know .

EDIT: I think the post by scouser73 will solve it.

---

### Post by teachop on 2009-12-30
Alas my computer is ATI graphics, I should have provided more details in my original post.  Thanks for the help anyway, I am going off to look for an equivalent utility for this hardware.

---

