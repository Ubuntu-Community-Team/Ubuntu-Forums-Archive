---
title: "Screensaver crashes system"
date: 2010-05-01
forum: General Help
---

### Post by Sevy on 2010-05-01
Im currently successfully using Lucid from an upgrade but with a couple of minor problems so far.
When I select certain screensavers my whole system crashes and have to hard boot.Floating Ubuntu works fine but for example GLslideshow crashes.
I also have a crappy purple splash screen with Ubuntu written for a couple of seconds.
Anyone experienced this or have a fix?
Thx

---

### Post by Sevy on 2010-05-02
bump

---

### Post by inearlygaveup on 2010-05-02
It crashes my Xubuntu 9.10.
I can't get back into the Screensaver tab to turn it off as it now crashes as soon as I open the screensaver preferences!
Perhaps someone knows a method of deselecting the activate screensaver button via the terminal.

Any idea's welcome

---

### Post by utnubuuser on 2010-05-04
Ditto - 

Ati video card

It's all the GL*** screensavers  - now that I've got one set I can't unset because I can't get in there to change it.

UPDATE: I managed to fix the crashing by going through Alt+F2, then gconf-editor, then apps, then gnome-screensaver, and setting the mode to "blank-only".
That allowed just enough time to quickly change the setting to one of the non-GL themes before crashing again, and on restart the screensaver dialog was accessible again.

---

### Post by inearlygaveup on 2010-05-04
Thanks NAGA it worked for me, I will keep away from the GL themes.
Also got your message about Ati cards, I am not sure what this one has (how do you find out)

---

