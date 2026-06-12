---
title: "Customize Nautilus keyboard shortcuts"
date: 2010-08-29
forum: General Help
---

### Post by veggen on 2010-08-29
Is there a way to customize the keyboard shortcuts for Nautilus? Namely, I want ctrl+n to create new folder and ctrl-m to create new text file. I searched for the answer but the only one that actually contained info refers to now obviously deprecated Prefs -> Appearance -> Interface entry (there's no such thing in Lucid).

Any ideas?

---

### Post by teranex on 2010-08-30
I was just Googling with the exact same question, so I'm also interested in the answer. I often make a new empty textfile in Nautilus, so it would be easy to be able to do this with the keyboard.

---

### Post by inameiname on 2010-08-30
Can't you just set custom ones through Applications -> System -> Preferences -> Keyboard Shortcuts ? I do this for quick keys to open a terminal, or the gnome-system-monitor, or whatever else I desire.

---

### Post by veggen on 2010-08-30
> **inameiname said:**
> Can't you just set custom ones through Applications -> System -> Preferences -> Keyboard Shortcuts ? I do this for quick keys to open a terminal, or the gnome-system-monitor, or whatever else I desire.
Well, no, not really. Those are system-wide shortcuts, and Nautilus shortcuts are not listed there.

It sounds almost magically absurd that you can't customize shortcuts. I mean, every file manager (apart maybe from Windows Explorer) lets you do this...

---

### Post by inameiname on 2010-08-30
Yeah. Guess nautilus just hasn't gotten around to figure out key shortcuts. 

Although, as an alternative, you can always use nautilus-actions and make a new action or two that does what you want, through the context menu. Not quite the same, but something.

---

### Post by veggen on 2010-08-31
This is really weird because the option used to exists up to (and including) Jaunty under Prefs -> Appearance -> Interface.
Is there a replacement for this somewhere else in the menu? It's hard to believe that a feature just silently disappered without any replacement...

---

### Post by inameiname on 2010-08-31
Looking in Nautilus, there are set key shortcuts for use in it, such as for creating a new folder and creating a new file. Here is the screenshot:

---

### Post by wonesix on 2010-10-02
it's quite weird that they removed the interface entry.
so now you have to go to gconf-editor, desktop > gnome > interface,
check "can_change_accels"

problem solved!

> **veggen said:**
> Is there a way to customize the keyboard shortcuts for Nautilus? Namely, I want ctrl+n to create new folder and ctrl-m to create new text file. I searched for the answer but the only one that actually contained info refers to now obviously deprecated Prefs -> Appearance -> Interface entry (there's no such thing in Lucid).

Any ideas?

---

### Post by veggen on 2011-02-19
> **wonesix said:**
> it's quite weird that they removed the interface entry.
so now you have to go to gconf-editor, desktop > gnome > interface,
check "can_change_accels"

problem solved!

I haven't seen this reply until now. Absolutely awesome tip! Thanks a million wonesix!

---

