---
title: "gnome shell and FGLRX drivers"
date: 2011-10-23
forum: General Help
---

### Post by aliasandy on 2011-10-23
Im on 11.10, and i installed gnome shell to get away from unity, but when i switched to gnome, it was fubar, as seen here [http://i.imgur.com/DDCRL.png](http://i.imgur.com/DDCRL.png) at which point i reasoned that the drivers may not be up to date, and i checked, and sure enought they werent, but all attempts to activate the driver failed and outputted to a log, text of which found here [http://pastebin.com/8Tjb8Zpg](http://pastebin.com/8Tjb8Zpg) any ideas as to how i can resolve these issues would be much appreciated.

---

### Post by kaldor on 2011-10-23
The proprietary AMD driver still has issues with GNOME Shell and there's no known fix as of yet. I'd recommend using the default Radeon driver if it's possible for your needs.

---

### Post by aliasandy on 2011-10-23
Any idea where i could find these drivers?

---

### Post by kaldor on 2011-10-23
> **aliasandy said:**
> Any idea where i could find these drivers?

The Radeon driver is what Ubuntu uses by default. If you installed FGLRX/Catalyst, then you will need to remove FGLRX and revert to Radeon. Annoyingly, this *can* cause some problems. 

Brief Documentation on Radeon driver [_here_]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by pazuzuthewise on 2012-02-19
The problem is that the open source Radeon driver is causing overheating (and fglrx does not), so this isn't really a solution. Because this overheating issue (10 degrees Celsius more with the kms radeon driver than with the proprietary fglrx), I am forced to not to use gnome-shell, having to use unity (which works well enough with fglrx).

---

