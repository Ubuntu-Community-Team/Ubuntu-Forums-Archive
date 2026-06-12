---
title: "Rhythmbox and iPod"
date: 2006-06-28
forum: General Help
---

### Post by jhorner on 2006-06-28
Is there anyway to change the program that opens when an iPod is connected?  Whenever I connect my ipod, it automatically opens Rhythmbox (which I don't use).  I was going to uninstall Rhythmbox but it also requires me to uninstall ubuntu-desktop...which probably isn't a good idea.

Any suggestions?

---

### Post by mlind on 2006-06-28
System > Preferences > Removable Drives and Media
(select multimedia tab) > untick checkbox from "Portable Music Players"

---

### Post by aysiu on 2006-06-28
You can uninstall *ubuntu-desktop*. It's not a real package--it's just a pointer to other packages: > **The Ubuntu desktop system**
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system). It'll come in most handy when you upgrade from Dapper to Edgy, but between now and that time, you don't really need it.

I think mlind is on the right track, but it sounds as if you want to change the application, not have the iPod not open at all. Just type something else instead of Rhythmbox.

---

### Post by jhorner on 2006-06-29
Thank you both for the suggestions.  I will try this tonite.

---

### Post by Kashirigi on 2006-07-06
Actually, there's a box on the second tab where you can just select (or not) which media player to use when your removable media is plugged in. You can still have it automounted.

I'm sorry I can't give you the exact details, but I'm using XFCE right now . . .

---

### Post by aysiu on 2006-07-06
[QUOTE=Kashirigi]Actually, there's a box on the second tab where you can just select (or not) which media player to use when your removable media is plugged in. You can still have it automounted.

I'm sorry I can't give you the exact details, but I'm using XFCE right now . . .[/QUOTE]
That's the attachment in my earlier post.

---

### Post by lixy on 2007-01-29
As mentionned before, go to System -> Preferences -> Removable media. Then click on the multimedia tab where "portable music player" appears at the bottom. All that's left is to replace rythmbox with gtkpod.

Rock on!

---

