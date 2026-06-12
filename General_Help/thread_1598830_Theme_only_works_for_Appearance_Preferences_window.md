---
title: "Theme only works for Appearance Preferences window"
date: 2010-10-17
forum: General Help
---

### Post by Essence on 2010-10-17
Hello,

I got a new computer recently, and just now installed 10.10. Everything was going great.... until when I enabled the Nvidia drivers and set my dual monitors. While things still work fine, it appears I have no theme set (Aside from the Window Border).

When I check in System->Preferences->Appearance it always shows the theme properly for this one window, while all other windows, and gnome panels etc appear to have no theme set (just use simple flat colours, low graphic mode etc).

Changing the theme (via the Appearance window) does not work, nor does a simple reboot.

Any ideas?

Bryan

---

### Post by Essence on 2010-10-17
I suppose I posted too soon....

I managed to find a solution to my own problem. For anyone else having this issue, here is what I did to resolve it.

Open The 'System Monitor'
Select the 'Processes' tab
Select 'gnome-settings-daemon' from the list
Right click, and end the process.
Open a new terminal, run 'gnome-settings-daemon'

And viola! The problem was solved, themes were applied again, and now upon restarts the themes are working each time.

Bryan

---

