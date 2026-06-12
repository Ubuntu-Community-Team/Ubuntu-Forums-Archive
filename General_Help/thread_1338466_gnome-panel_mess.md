---
title: "gnome-panel mess"
date: 2009-11-26
forum: General Help
---

### Post by H4F on 2009-11-26
Hi all.
Recently my gnome panel is in total mess. Even if I  place the icons in the right places and lock them up after a restart everything is in a mess again.

any one experiencing same problem. any suggestion solution ?

---

### Post by Shukuyir on 2009-12-02
I'm having the same problem with everything getting messed up. Also what happened was that I decided to move a panel to a different position but when I restarted or logged out and logged back in again the panel had moved back to its last position again. I don't know why but everything seems to be alright now but it still happens randomly and when it does it gets really annoying needing to reposition everything again.

---

### Post by Vajra Vrtti on 2009-12-02
Although I never needed it, I have the following receipt to fix the gnome panels:

> **Restore Ubuntu Panels Back To Their Default Settings**
[I]
gconftool - -recursive-unset /apps/panel 
rm -rf ~/.gconf/apps/panel
pkill gnome-panel[/I]

Both top and bottom panels will appear (if missing) with their default settings.

---

### Post by H4F on 2009-12-02
> **Vajra Vrtti said:**
> Although I never needed it, I have the following receipt to fix the gnome panels:

But what about all panels you have setup ? will they restore in theyre places too ? if no than this is not a fix because it will take me again 5 min to setup everyting in place.

---

### Post by williamson389 on 2009-12-03
The script works great and yes they are in the default position.

I have another question-
While customizing my desktop i deleted the internet applet and cant find anyway to get it back.  any ideas?

---

### Post by RJ12 on 2009-12-12
it should be in the Notification Applet set

---

