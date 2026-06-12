---
title: "replace gnome-terminal with lxterminal?"
date: 2010-03-20
forum: General Help
---

### Post by pythonscript on 2010-03-20
Is there a way to completely replace my gnome terminal with the lxde terminal (lxterminal)? I use the nautilus open terminal extension quite a bit, and I'd like to set this to use the lxterminal, but I'm not sure how. Is this possible? Can I just remove gnome-terminal, or will that remove too many dependencies? Thanks!

---

### Post by dcstar on 2010-03-20
> **pythonscript said:**
> Is there a way to completely replace my gnome terminal with the lxde terminal (lxterminal)? I use the nautilus open terminal extension quite a bit, and I'd like to set this to use the lxterminal, but I'm not sure how. Is this possible? Can I just remove gnome-terminal, or will that remove too many dependencies? Thanks!

In the Alternatives Configurator (galternatives) there is an entry for x-terminal-emulator, that can be changed to whatever terminal packages you have installed.

---

### Post by pythonscript on 2010-03-21
I ran

```
sudo update-alternatives --config x-terminal-emulator
``` and selected lxterminal, but when I run open terminal here from nautilus (after I reboot) the gnome terminal still comes up. What am I doing wrong? I also tried the gui, with the same result. Thanks!

---

### Post by pythonscript on 2010-03-23
> **dcstar said:**
> In the Alternatives Configurator (galternatives) there is an entry for x-terminal-emulator, that can be changed to whatever terminal packages you have installed.

Is there anything else I can try besides this option? This simply has no effect on what nautilus-open-terminal uses; when I right click and select Open In Terminal, the gnome-terminal still comes up. How can I change this? I really don't want to use the gnome terminal in place of lxterminal. Thanks!

---

