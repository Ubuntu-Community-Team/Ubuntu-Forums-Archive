---
title: "Simple panel question (I hope)"
date: 2009-12-24
forum: General Help
---

### Post by alehman42 on 2009-12-24
I accidentally removed the network manager and volume control icons from a panel on my desktop, and I'm embarrased to say I can't figure out how to put them back.

I'm assuming this is a simple fix, but if someone could direct me as to how to do so, I'd much appreciate it.

---

### Post by running_rabbit07 on 2009-12-24
Right-click on the panel then click add to panel, then add network manager, notifications, and volume control. If there is no selection for volume control. Open the main menu, find volume control and drag and drop it on the panel.

Hope this helps. Never be ashamed to ask for help unless you are searching for the any key.:)

---

### Post by alehman42 on 2009-12-24
Sorry, should've been more specific about what I'd tried.

I know how to add buttons to the top panel, but neither the network manager nor the volume control are listed among the options to add (after right clicking and choosing 'add to panel').

I tried looking in the main menu for the volume control...the closest I found was sound preferences, which I can add to the panel just fine, but isn't quite what I was looking for.  That launches the entire gnome-volume-control program, while I was just looking to replace the slider bar controlling the volume.

Essentially, I want to restore my top edge panel to the default.  Any suggestions as to the best way to do so?

---

### Post by howefield on 2009-12-24
> **alehman42 said:**
> I want to restore my top edge panel to the default.

Try opening a terminal and typing the following.

```
rm -r ~/.gconf/apps/panel
```

This will remove the current configuration and be rebuilt when you log out and back in.

You don't have to remove the folder, if you prefer you could rename or simply move it, so that you can put it back if it doesn't go to plan.

This will put both top and bottom panels back to default.

---

### Post by sentythee on 2009-12-24
Add Notification Area to your panel.

---

### Post by alehman42 on 2009-12-24
Thank you!

I knew there had to be a simple solution I missed...

---

### Post by erniej on 2009-12-25
Many thanks from a lurker as well. That's been driving me nuts for the past few days.

---

