---
title: "Xubuntu 11.04 trashed by updates"
date: 2011-10-26
forum: General Help
---

### Post by sgharp on 2011-10-26
Hi Guys,

I just updated one of my machines running Xubuntu 11.04 with the recommended updates.  Note, this was NOT an upgrade to 11.10.  

After the updates, my desktop only has 1 workspace instead of the 6 that it had previously.  Also, when applications are running they no longer have the -+x icons in the top right of the titlebar.  When I try to use the Settings Manager to correct desktop settings, the screens in the SM appear blank.

Has anyone else experienced this?

Does anyone have a suggestion on how to fix it?

Thanks...

---

### Post by Toz on 2011-10-26
Sounds like the Window Manager and possibly the desktop manager are not running/crashed. Try Alt+F2 then:
```
xfwm4 --replace
```
...to restart the window manager. This should bring back the window decorations, icons and content in desktop settings applets.

If this also doesn't fix the workspace issue, try Alt+F2 again and:
```
xfdesktop --reload
```

---

### Post by sgharp on 2011-10-27
> **Toz said:**
> Sounds like the Window Manager and possibly the desktop manager are not running/crashed. Try Alt+F2 then:
```
xfwm4 --replace
```...to restart the window manager. This should bring back the window decorations, icons and content in desktop settings applets.

If this also doesn't fix the workspace issue, try Alt+F2 again and:
```
xfdesktop --reload
```

Wow!  That worked perfectly.  Thanks a bunch.  I owe you big time....

---

### Post by Toz on 2011-10-27
Glad to hear. Can you please mark this thread solved using the "Thread Tool" link above?

---

