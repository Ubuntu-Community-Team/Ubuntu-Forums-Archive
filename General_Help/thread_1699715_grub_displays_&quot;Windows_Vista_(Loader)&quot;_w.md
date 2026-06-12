---
title: "grub displays &quot;Windows Vista (Loader)&quot; which I didn't install"
date: 2011-03-04
forum: General Help
---

### Post by petrov_go on 2011-03-04
Hello! I can't understand what for a bug is it. I'll describe the situation from the very beginning.

On my notebook there was a preinstalled OEM Windows 7 Home Basic (disk C, sda1). 
I installed Ubuntu 10.10 on disk D, and was not using Windows 7 any more, although the "seventh" was present in main loading menu and in grub menu.

2 days ago I discovered, that** in grub menu appeared  "Windows  Vista (Loader) - sda1"** ! **I didn't install it,** and I'm sure that nobody else had access to my notebook.
"Windows 7  (Loader)" now links to sda2.

When I try to run this strange "Windows  Vista (Loader)", appears the Windows loading screen, than the empty Windows desktop background, and than the system reboots.

Please help to understand, what is it. 

[LIST=1]
[*]**How can Windows  Vista (Loader) appear in grub, if nobody installed it?**
[*]Can it be an imitation of Vista loader, made by some malware?
[*]How to remove this item from grub?
[/LIST]

Thank You in advance!

---

### Post by wilee-nilee on 2011-03-04
Take a screen shot of gparted and post it. You have to install gparted on a installed ubuntu, it is on the live cd though.

---

### Post by petrov_go on 2011-03-04
ok, I'll make a screenshot and post it here, a bit later

---

### Post by H-Racky on 2011-03-04
I'm 99,48% sure that the **"Windows Vista (Loader)" **represents the files to repair the Windows 7 (system files to restaure W7 to it's original format).

---

### Post by frenziedfemale on 2011-03-04
I have the same thing, the Vista loader is part of the recovery system for Windows 7.

---

