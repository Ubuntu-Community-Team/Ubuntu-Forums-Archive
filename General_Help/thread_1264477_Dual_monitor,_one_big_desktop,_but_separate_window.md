---
title: "Dual monitor, one big desktop, but separate window list"
date: 2009-09-12
forum: General Help
---

### Post by Farenji on 2009-09-12
I'm using ubuntu with two monitors, using nvidia twinview. So I have one big desktop of 2720x1024, I can move windows from one screen to the other etc., but the window list of the two monitors is separate. So I need two panels with window lists, for each screen one. This is not very practical and also it used to be different; there used to be only one window list for the two screens. I guess this is configurable and it must be something I changed (as I'm the only user of this pc), but to be honest, I forgot what I did and how, and now I don't know what to change where to revert the setting. I looked everywhere in the gnome control panel, and of course also in the nvidia X server settings panel but I can't find anything that does the trick. Any help?

---

### Post by P4man on 2009-09-12
when you right click the (edge of the) window list on the panel, properties, you have an option to show windows from all workspaces. Does that help?

---

### Post by Farenji on 2009-09-12
> **P4man said:**
> when you right click the (edge of the) window list on the panel, properties, you have an option to show windows from all workspaces. Does that help?

A bit - in the sense that all apps are shown in one window list. But i do have 4 virtual workspaces, and I prefer to have only the applications from the current workspace in my window list... so there must be another solution.

---

### Post by wojox on 2009-09-12
So when you click on Window List Preferences > Window List Content > Show windows from the current workspace it won't work?

---

### Post by P4man on 2009-09-12
have a look here perhaps:
[http://ubuntuforums.org/showthread.php?t=766027](http://ubuntuforums.org/showthread.php?t=766027)

especially the last post.

---

### Post by corncob on 2009-09-12
> **Farenji said:**
> I'm using ubuntu with two monitors, using nvidia twinview. So I have one big desktop of 2720x1024, I can move windows from one screen to the other etc.,

I have the exact same setup for my daughter but I don't know what you mean by "window list" --- something I don't use maybe or have a different name for?

---

### Post by Farenji on 2009-09-12
> **P4man said:**
> have a look here perhaps:
[http://ubuntuforums.org/showthread.php?t=766027](http://ubuntuforums.org/showthread.php?t=766027)

especially the last post.

Thanks! That last post indeed was the solution. I found out I had a second (nearly invisible) window list applet on my panel. Removed it and all is well now. :)

---

### Post by sidragon on 2011-05-05
For those who found this discussion first, follow [this quote from the other thread]("http://ubuntuforums.org/showpost.php?p=7633792&postcount=11").

> **oi_antz said:**
> Have a real close look at your panels and remove any extra "window list" panel items that may have been added. Once I had done that, the sole window list now lists all windows in the current workspace, even windows positioned on the right monitor.

That will solve it!

---

