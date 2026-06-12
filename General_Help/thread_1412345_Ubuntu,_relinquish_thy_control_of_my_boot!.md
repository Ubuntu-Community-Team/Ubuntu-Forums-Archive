---
title: "Ubuntu, relinquish thy control of my boot!"
date: 2010-02-21
forum: General Help
---

### Post by hydrotemplar on 2010-02-21
How do I go about getting Ubuntu to not try to maintain or update or add entries to my Grub?

On another install I have a standalone boot partition on which I keep my menu.lst and kernels updated manually, but when I do anything with apt, it complains about not being able to upgrade the kernel in my boot config (even though it's running a newer version than what it's complaining about lol)  I don't want to have to go through that on this install, so I'm asking before I try anything : )

Basically I want it to still put new kernels in my boot partition but not try to update grub with it and most importantly, Leave Me Alone about it.

Thanks,
David

---

### Post by Pjotr123 on 2010-02-21
What you want is probably impossible, because adding new kernel lines automatically after updates, can only be done by update-grub, as far as I know. update-grub is being triggered automatically after a kernel update; I wouldn't know if it's feasible to block that. I suppose not.

The new Grub 2 that comes with Ubuntu 9.10 is a lot less easy to configure manually, than the old Grub 1. You're supposed to do everything with scripts nowadays, instead of editing good old [COLOR="Blue"]menu.lst[/COLOR]. Nowadays, [COLOR="Blue"]Grub.cfg[/COLOR] is the new magic, which has turned entirely Automagic (as opposed to [COLOR="Blue"]menu.lst[/COLOR], which was only partly Automagic).

I deal with Grub 2 as follows, because messing with scripts is too much ado for me:
- I uninstall old kernels, so as to keep the number of Grub menu lines down.
- I sabotage the Windows Recovery partition on my laptop, by renaming the file [COLOR="Blue"]ntldr[/COLOR] on that partition, into [COLOR="Blue"]ntldrx[/COLOR]. Then [COLOR="Blue"]sudo update-grub[/COLOR] and the bugger is gone. :)

In the near future, life with Grub will become a lot easier, when startupmanager will get more options.

---

### Post by hydrotemplar on 2010-02-21
Thanks for the speedy reply, but I use grub legacy, complete with the very nice menu.lst : )
So manual configuration isn't the problem, the problems are a) Ubuntu trying to hijack my configuration and b) Ubuntu whining when it's unable to do so

: )

---

### Post by hydrotemplar on 2010-02-22
bump

---

### Post by mechro on 2010-02-22
I don't know whether this will work...

In your **menu.lst** try moving the lines...

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
```

to just below the line...

```
## ## End Default Options ##
```

This will mean there are no entries for any kernel updates to work on but I'm not sure if it will cause an error.

Make sure you have a back-up of **menu.lst** in case you have to restore.

---

