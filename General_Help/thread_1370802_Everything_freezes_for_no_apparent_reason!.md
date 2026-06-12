---
title: "Everything freezes for no apparent reason!"
date: 2010-01-02
forum: General Help
---

### Post by murt on 2010-01-02
I was moving my top panel to sit on top of my bottom panel, for some reason, and then everything just froze. I had totem playing a avi film at the time, too, even if I don't think that's of interest. Nothing except my mouse was working, my background was still there and the icons on my desktop was too left on the screen, but I couldn't interact with them. All the panels went blank.

Then I ctrlaltdelete-restarted from tty1 and opened a xterm-session and posted this (after testing the fail-safe gnome, which didn't work a bit better).

If it's of interest, I use a HP laptop with an Intel x86 processor and an Intel graphics card.

---

### Post by warfacegod on 2010-01-02
Freezing is usually caused by either CPU overheating or corrupted RAM modules.

---

### Post by murt on 2010-01-02
> **warfacegod said:**
> Freezing is usually caused by either CPU overheating or corrupted RAM modules.

Oookey, but how to fix it? I don't think it's an overheated CPU, since I'm using the computer now again, but gnome still ain't working. And the computer is rebooted, the ram should have been flushed or what it's called, shouldn't it?

---

### Post by murt on 2010-01-02
FIXED IT!
First I placed ~/.gnome2 and some other folders in a new folder, so they wouldn't have effect. Then I killed all my users processes, therefore kicking myself out and then I logged in in gnome, and all my settings were of course gone but it works again.

---

### Post by warfacegod on 2010-01-02
Sounds like you inadvertantly turned something off that you shouldn't have. Perhaps a conflict in settings that was somehow triggered by moving your panel bar. Although the playing avi file makes me think that your video card got overloaded. I don't use Totem but when my media player asks for too much resource, it just closes itself (64MB video card) and it's always when compiz is on.

---

