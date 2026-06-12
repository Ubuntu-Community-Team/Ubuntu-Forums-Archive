---
title: "NetworkManager Missing?"
date: 2009-07-23
forum: General Help
---

### Post by Codix121 on 2009-07-23
I'm running jaunty 9.04 and I was messing with my icons on my panel,
and accidently erased my NetworkManager, and when I click ADD TO PANEL,
NetworkManager doesn't show up, I've tried to open it through terminal using

```
NetworkManager
```

but nothing opens and I can't connect to internet anywhere outside my home,
it logs into my wifi at home because it's autoset but when i go else where,
it won't bring up the panel to connect to any local wifi :(

---

### Post by spiderbatdad on 2009-07-23
What you are looking for is called "notification area." This is where network manger lives.

---

### Post by mcduck on 2009-07-23
It's not available for adding to panel because it's not a panel applet. ;)

It's just a program that runs in the background and puts an icon in the Notification Area-applet.

So, first thing to do is make sure that you still have the Notification Area-applet in your panel. After that, if the Network Manager still doesn't show, press Alt-F2 and run "nm-applet".

---

### Post by Codix121 on 2009-07-23
Wow im so noob! thank you so much! I figured it was probably something really easy >.> thank you!

---

### Post by Ravenheart on 2009-07-31
> **mcduck said:**
> It's not available for adding to panel because it's not a panel applet. ;)

It's just a program that runs in the background and puts an icon in the Notification Area-applet.

So, first thing to do is make sure that you still have the Notification Area-applet in your panel. After that, if the Network Manager still doesn't show, press Alt-F2 and run "nm-applet".


Thanks for the information. Spent a couple of hours last night trying to figure out where my network applet went.  Restored it in a couple of minutes after searching the forums.  Still don't know how I deleted the notification area though!

---

