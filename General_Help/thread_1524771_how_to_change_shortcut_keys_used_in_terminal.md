---
title: "how to change shortcut keys used in terminal?"
date: 2010-07-05
forum: General Help
---

### Post by MountainX on 2010-07-05
I want to reassign ctrl-shift-C and ctrl-shift-V. How is that done? (I'm using a Mac keyboard and I'd like to take advantage of the command key to avoid having to hit two modifiers.)

---

### Post by sisco311 on 2010-07-05
gnome-terminal -> Edit -> Keyboard Shortcuts...

konsole -> Settings -> Configure Shortcuts...

xfce4-terminal  -> Edit -> Preferences -> Shortcuts

---

### Post by MountainX on 2010-07-05
> **sisco311 said:**
> gnome-terminal -> Edit -> Keyboard Shortcuts...

konsole -> Settings -> Configure Shortcuts...

xfce4-terminal  -> Edit -> Preferences -> Shortcuts

If that answers my question, I do not understand exactly how. I need to change the ways keys are mapped **in the terminal**.

---

### Post by MountainX on 2010-07-05
I've been "researching" this for the last couple hours. Here's what I learned so far. It looks like I need to create this file:
~/.inputrc

As for the content in that file, I have not found a reference yet...

I also learned about bind -P. It lists all editing key bindings, but it does not list the binds for Ctrl-C.

I want to map Ctrl-C and Ctrl-V to copy and paste in the terminal (without the shift key). I'll map the terminate command to Ctrl-Shift-C. 

And I want to map undo to Ctrl-Z (instead of undo mapped to "\C-x\C-u", "\C-_"). For background, I'll come up with a new shortcut.

So, still looking for help...

---

