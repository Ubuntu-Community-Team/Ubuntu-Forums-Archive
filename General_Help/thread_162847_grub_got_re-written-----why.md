---
title: "grub got re-written-----why?"
date: 2006-04-19
forum: General Help
---

### Post by adambeazley on 2006-04-19
Whats up everyone?

Well I edited my grub boot loader so that only the following would show:

Windows xp
Ubuntu
Ubuntu(recover)
memtest86

So I had it set up like that with xp booting as the default in 5 seconds. Now for some reason, one day (i dont even remember which day) the menu.lst got re-written and the origional menu list of OS's to be booted got added to my list. So now I had:
Ubuntu
ubuntu older kernal
ubuntu
ubuntu(recovery)
windows xp
ubuntu
memtest
ubuntu (recovery)

So anyway, I changed it back to what I had before and its working fine, but Im just curious why tht happened, and weather it will happen again.
thanks
Adam

---

### Post by krusbjorn on 2006-04-19
Menu.lst is regenerated when you update the kernel. Anything between where it says that the automagical list starts and stops will be removed/rewritten. Entries outside of that section will be left alone though.

---

