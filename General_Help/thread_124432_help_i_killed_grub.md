---
title: "help: i killed grub"
date: 2006-02-01
forum: General Help
---

### Post by pedwards on 2006-02-01
so after having a perfecly healthy duel boot i re installed widows on the c drive. 
now grub will not load and my comp just goes to windows.
what can i do

i have dell laptop inspiron 1150

:cry: :cry: :cry: :cry: :cry:

---

### Post by Elrohir on 2006-02-01
had the same problem once... try this:

1.- boot with install CD
2.- when it asks for the option to boot, type "rescue" (without the quotes), enter
3.- when it loads a terminal (bash I believe it is), type "sudo grub-install /dev/hda#" (without the quotes); # is the partition where Ubuntu is...

---

