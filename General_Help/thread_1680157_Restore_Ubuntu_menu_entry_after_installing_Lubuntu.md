---
title: "Restore Ubuntu menu entry after installing Lubuntu"
date: 2011-02-02
forum: General Help
---

### Post by blazemore on 2011-02-02
Thought I'd install Lubuntu to try it out.
It's lovely, but I need to go back to Ubuntu sometimes.
However, the menu entry for it has disappeared!

I don't know the first thing about grub2 (would have been trivial in Grub) and can't make head nor tail of any of the configuration files.

How can I re-add it? I've tried update-grub, to no avail.

---

### Post by Quackers on 2011-02-02
From inside the Lubuntu desktop, open a terminal and run sudo update-grub and watch to see if the other installation is picked up. If it is, reboot and you should be good.
If it isn't picked up, go to synaptic package manager and in the search box enter os-prober. When it appears in the main window does it have a green box next to it (in other words, is it installed)? If not, install it and run sudo update-grub again.

---

