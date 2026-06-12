---
title: "Editing Boot Loader"
date: 2011-04-24
forum: General Help
---

### Post by lithops on 2011-04-24
I have a dual boot system - Lucid Lynx and Windows XP. The boot loader now displays kernel choices from version 24 up to the present (32) and at the end of the list the Win XP choice is displayed. I would like to remove the displays for versions 24 to 30.

How do I do that?

Searched for a previous thread but unsuccessful.

---

### Post by Quackers on 2011-04-24
Delete the previous kernels with synaptic package manager. Enter 2.6.2*  into the search box, then in the main window scroll through selecting complete removal for everything except the kernel(s) that you want to keep.
Do the same with 2.6.3* if you want to. Then apply the changes.
You must leave at least the currently used kernel! :-)
When they are deleted, run sudo update-grub in a terminal, to amend the grub menu.

---

