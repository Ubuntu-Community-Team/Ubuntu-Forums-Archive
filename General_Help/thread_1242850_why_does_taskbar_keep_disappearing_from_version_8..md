---
title: "why does taskbar keep disappearing from version 8..10?"
date: 2009-08-17
forum: General Help
---

### Post by rutiezer on 2009-08-17
RE: ubuntu version 8.10

I now know that when the taskbar disappears one can run the command 
   xfce4-panel
from a terminal to restore it.

Why when I log in, why is the taskbar sometimes missing and not other times?

How do I start a terminal when there is no access to Applications,
then Accessories then Terminal?

How do I keep the taskbar from disappearing in the first place.

---

### Post by john.nicholls on 2009-08-18
Are you saving your session? Make sure that Settings Manager | Session and Startup | General | Logout Settings | Automatically save session on logout is checked.

You can open the Xfce terminal from the Run dialog (alt-F2) by typing
```
exo-open --launch TerminalEmulator
```

---

### Post by rutiezer on 2009-08-24
I found it and checked it.
"Save sessions on logout" was not checked as part of initial installation.

Thanks John.

Howard

---

### Post by jim-fwb on 2009-09-23
Just updated and the xfce taskbar was gone tried the above suggestion, which restored the taskbar ... until the terminal was closed.  Tried again, and went to settings before closing.

According to the settings manager the taskbar was there, and when I closed the setings manager, this message appeared on the terminal:

(xfce4-settings-manager:2125): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

Ideas anyone?  The panel is not exactly critical & I have fluxbox installed.  KDE was installed, too, but it is not showing up as an option in KDM.  ugh!

---

### Post by jim-fwb on 2009-09-24
Answered my own question.  Some form of interaction between fluxbox and xfce, I'd decided to try an option in fbx to use xfce desktop for file mgt.  That seems to have blocked its use in xfce.  When I restore things to normal in fbx, xfce was restored, too.  Still no kde, seems to be a different questional together. Several KDE components were flagged for removal in the dist-upgrade.

---

