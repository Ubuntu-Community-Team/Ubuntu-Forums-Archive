---
title: "ctrl + alt + d stopped working"
date: 2010-10-14
forum: General Help
---

### Post by Paul41 on 2010-10-14
I have been using Ubuntu for many years now and pressing ctrl + alt + d used to minimize all windows and show the desktop, but this stopped working with 10.10.  I checked keyboard shortcuts but don't see a way to turn it back on there.  Anyone have any ideas how to get this back?

---

### Post by mc4man on 2010-10-14
Seems to be working here - only thing I've touched is changing the non-functional Alt+PrtScr to Ctrl+PrtScr

Is listed in gconf-editor - metacity - global_keybindings

---

### Post by Paul41 on 2010-10-14
Thanks, I checked in gconf-editor and it has been changed to <Super>d so I'm good now that I know what it is.

---

### Post by rungss on 2010-12-07
> **Paul41 said:**
> Thanks, I checked in gconf-editor and it has been changed to <Super>d so I'm good now that I know what it is.

Thanks Man, you saved my Day.


The Config settings you would be looking at is /apps/metacity/global_keybindings/show_desktop

It changed from Ctrl+Alt+D to Super+D After I upgraded to Maverick It seems.

---

