---
title: "Alternative logout applet needed"
date: 2010-05-07
forum: General Help
---

### Post by mterlouw on 2010-05-07
I'm having trouble finding a suitable logout applet in Lucid.  The default applet has a nice menu with the things I need: Logout, Reboot, Shutdown, and Suspend.  But it's attached to the instant messenger menu which I can't remove (by design, I think).  I want to get rid of this menu because it's just a useless grey square / username and wastes precious space on the panel.

indicator-session and "Log out..." applets don't seem to have the Suspend, Shutdown and Reboot options.  (Those options appear to have been removed from the System menu in Lucid as well.)

Is anyone aware of a log out applet that is essentially the right menu of indicator-applet-session, or a way (e.g., gconf) to disable the left (instant messenger) menu so it doesn't take up any panel space?  Or has anyone yet forked indicator-applet-session to make it configurable?

Thanks

---

### Post by TheCowGod on 2010-05-07
I took all that stuff off and use gnome-do. Its not a panel applet but you can open it at any time by typing <super> + 'space' and just start typing and it will do pretty much anything. <super> + 'space' and 'lgo' and it will log out for you. Its like the alt + f2 'Run Application' dialog on steroids.

---

### Post by Aearenda on 2010-05-07
In 10.04, if you uninstall the indicator-me package, the IM stuff will disappear from the panel on your next login. You can still shut down etc.

OR, just remove the indicator-session-applet from the panel; the shutdown entries will then appear by magic on the system menu. But I think taking out indicator-me is the nicer way to go.

Also, if you don't need it for any other reason, uninstalling indicator-messages will remove the envelope icon but leave the other indicators in place, such as the volume control.

---

### Post by mterlouw on 2010-05-07
> **Aearenda said:**
> In 10.04, if you uninstall the indicator-me package, the IM stuff will disappear from the panel on your next login. You can still shut down etc.

That did exactly what I needed.  Thanks, Aearenda!

---

