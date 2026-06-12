---
title: "Use notify-osd  to show system updates?"
date: 2009-11-27
forum: General Help
---

### Post by anjilslaire on 2009-11-27
Since Jaunty, I've used the following to disable the "new" behavior of update-manager and restore it to showing system updates in the system tray where I like them:
[http://www.ubuntumini.com/2009/05/remove-pop-up-update-manager.html](http://www.ubuntumini.com/2009/05/remove-pop-up-update-manager.html)
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

This also triggers notify-osd to show the updates using the same system as most everything else.
However, doing this in Karmic causes the updates to show up in the system tray as desired, but they don't appear in the OSD.

Thoughts on how to get system updates to be displayed by notify-osd?

Thanks

---

### Post by kerry_s on 2009-11-27
:lolflag: i didn't even realize how much i hated that till i tried linux mint, the update applet is much better.
i personally don't like the osd notifications & always switch it back to the old style.

---

### Post by VCoolio on 2009-11-27
Don't know how change settings to get the desired behavior, but here is a command that will work:

```
notify-send -i synaptic "Updates" "There are $(aptitude search ~U | wc -l) updates available"
```

---

