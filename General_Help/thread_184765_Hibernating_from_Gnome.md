---
title: "Hibernating from Gnome"
date: 2006-05-30
forum: General Help
---

### Post by oneandoneis2 on 2006-05-30
I installed Kubuntu on my laptop over the weekend. Was quite impressed that hibernation worked out-of-the-box after just checking a few boxes in KDE's config windows.

But I'm not actually a big KDE fan, so I installed Gnome. And of course, *KDE* being set up to suspend-to-disk isn't doing me any good from there. And a quick hunt through the menus isn't turning up anything obvious.

I daresay I'm missing something massively obvious, but Google isn't helping me, and neither are my usual Linux habits - I'm used to Gentoo, FVWM and vi, not all these DE menus...

So: Is there a simple way to tell Gnome to hibernate when I close the laptop lid? And if so, what is it?

---

### Post by Ubuntuud on 2006-05-30
Power manager, System > Preferences > Power Management.

At least that's how it goes in Dapper. If you can't find the option, you could wait a week for Dapper... I'm not running Breezy at the moment, so I can't look for it myself.

---

### Post by bruce89 on 2006-05-30
Dapper will be here in 2 days, or to upgrade now, ```
gksu "update-manager -d"
```

---

### Post by oneandoneis2 on 2006-05-30
There was no "power management" option.

So I installed "gnome power manager", which I hadn't realized wasn't installed. That gave me the menu option.

But it gives me a window that gives me one option: How many minutes before the computer goes to sleep. Sadly ,that doesn't help with suspending to disk on-cue...

---

### Post by oneandoneis2 on 2006-06-01
Kinda academic now that Drake is out, but for completeness:

Switching from KDM to GDM gave me an option in the Gnome logout window to Hibernate the PC..

---

### Post by ThomasAdam on 2006-06-01
[QUOTE=oneandoneis2]Kinda academic now that Drake is out, but for completeness:

Switching from KDM to GDM gave me an option in the Gnome logout window to Hibernate the PC..[/QUOTE]

I assume that by "hibernate" you mean somesort of suspend-to-disk thing?  This is generally what acpid is for if your laptop supports it, along with swsusp.

-- Thomas Adam

---

