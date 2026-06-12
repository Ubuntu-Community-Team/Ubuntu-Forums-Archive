---
title: "gnome-terminal and gconftool"
date: 2010-11-27
forum: General Help
---

### Post by planetofdeviants on 2010-11-27
After a fresh boot of a Live CD, how do I use the gconftool command to edit:

```
 /root/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml
``` ??

I tried:

```
mint@mint ~ $ sudo su
mint mint # gconftool --load /media/scripts/gconf/gnome-terminal/custom.xml
mint mint # gnome-terminal
```No changes were made after I opened a new gnome-terminal..  It works fine if I'm not in superuser mode and makes the changes to
```
 /home/mint/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml
```just fine.

What am I not getting here?

---

### Post by asmoore82 on 2010-11-27
1. You shouldn't `sudo su` on *buntu.
2. You shouldn't run any graphical apps as root unless they are designed for it.
(Example: `synaptic` is designed for it, "Ubuntu Software Center" is not.)
3. Even when you do run a graphical app as root, you should use `gksudo` or `kdesu`, never `sudo` or `su`

---

### Post by planetofdeviants on 2010-11-27
> **asmoore82 said:**
> 1. You shouldn't `sudo su` on *buntu.
2. You shouldn't run any graphical apps as root unless they are designed for it.
(Example: `synaptic` is designed for it, "Ubuntu Software Center" is not.)
3. Even when you do run a graphical app as root, you should use `gksudo` or `kdesu`, never `sudo` or `su`

I tried your solution.  When I Alt-F2 to run the script with these commands using gksudo as you've said, it doesn't run.  My mouse just turns into a crosshair until I click it. Sudo atleast does something.

Since I intend to be editing roots files, would it matter anyway?

---

