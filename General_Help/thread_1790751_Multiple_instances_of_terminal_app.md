---
title: "Multiple instances of terminal app?"
date: 2011-06-25
forum: General Help
---

### Post by dhave-dhave on 2011-06-25
How can I make it so that I can open multiple new instances of the terminal app by clicking on the corresponding icon? I'm running 11.04 with Gnome 3.

Thanks.

---

### Post by Chrissss on 2011-06-25
Click with the middle button on the icon :)

---

### Post by dhave-dhave on 2011-06-25
> **Chrissss said:**
> Click with the middle button on the icon :)
Great! Thanks. Now, is there a way to make the new Terminal instances open in tile fashion rather than in new workspaces?

---

### Post by dhave-dhave on 2011-06-28
> **dhave-dhave said:**
> Great! Thanks. Now, is there a way to make the new Terminal instances open in tile fashion rather than in new workspaces?
Anybody?

---

### Post by VCoolio on 2011-06-28
Difficult. I'd create a new launcher to open your terminal app with tmux running, and configure tmux to open two (or more) shells at a time.

Else you'd have to open two terminals with something to distinguish them, like, set a class or name, then configure for example devilspie to set the coodinates on your screen for both, using class/name as identifier.

---

### Post by dhave-dhave on 2011-06-28
> **VCoolio said:**
> Difficult. I'd create a new launcher to open your terminal app with tmux running, and configure tmux to open two (or more) shells at a time.

Else you'd have to open two terminals with something to distinguish them, like, set a class or name, then configure for example devilspie to set the coodinates on your screen for both, using class/name as identifier.
Thanks, VCoolio. I'll give those ideas a try.

When I used KDE (with another distro), multiple instances of my terminal app (Konsole) would open in tile fashion by default. I'm guessing this behavior is specific to the desktop environment or window manager rather than to the distro. Am I right?

Thanks again.

---

