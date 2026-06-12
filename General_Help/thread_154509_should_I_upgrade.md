---
title: "should I upgrade?"
date: 2006-04-03
forum: General Help
---

### Post by lbmounse on 2006-04-03
I'm running hoary on an old 500 MHz, 128 M ram PC.   
It runs a little slow, of course.
If I upgrade to breezy, will it be slower?
Is breezy more or less streamlined than hoary?
I will probably be upgrading the ram shortly.

---

### Post by taurus on 2006-04-03
Always backup your important data before you upgrade.  However, I would strongly recommand you use Xfce, fluxbox/blackbox, or other small window managers since you only have 128MB of RAM.  If you run Gnome, then your system would be slow, real slow...  Just change from hoary to breezy in /etc/apt/sources.list and run
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by frodon on 2006-04-03
I advice to follow those instructions, it worked nice for me at the time : [https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29](https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29)

---

### Post by mips on 2006-04-03
Personally I would not upgrade now. Breezy will not make things faster. Try a different desktop/windows manager as suggested above.

Or wait for Dapper, do a server install. Install a light Windows manager and only add the packages you need. This should work well.

Dapper is still in Alpha stages but I must admit that it is pretty stable as far as I'm concerned. Only do this if you feel comfortable doing it or have the time to sort out possible issues.

It would be nice if you could stick some more ram into the machine, 256-512MB should make a nice differance.

---

### Post by lbmounse on 2006-04-03
Okay, if I max out the ram (the machine can handle 512 MB), would an upgrade to breezy be reccommended, or should I just wait for dapper?

---

### Post by frodon on 2006-04-03
It's up to you, i have personally a 700Mhz with 512MB of RAM and i use gnome with the xfce window manager and all is ok for me.
Why not make a ghost of your ubuntu partition and try the update then revert it back if it doen't fit your needs.

---

### Post by az on 2006-04-03
[QUOTE=lbmounse]Okay, if I max out the ram (the machine can handle 512 MB), would an upgrade to breezy be reccommended, or should I just wait for dapper?[/QUOTE]
More ram will make things faster.

You can dist-upgrade now to breezy.  Breezy may be a little faster than hoary.  When Dapper is released, you can dist-upgrade to that.

Dapper is faster than Breezy.

If you have the disk space, you don't have to reinstall to use al lighter desktop.  You can install icewm (install the menu package, too, to make your life easier) and then log out.  Change your session so that you log back into icewm.

If you don't like it, log back out and change your session back to gnome.  You can try xubuntu-desktop like that, too.

I would reccommend you dist-upgrade to breezy for the time being, anyway.

---

### Post by mips on 2006-04-03
Either way, if you increase the ram things will run faster. Adding more ram never hurts. 512MB should be relatively cheap but I don't know your present setup.

---

### Post by lbmounse on 2006-04-04
I'm also running breezy on an 850 MHz, 256 MB laptop, and it doesn't seem too slow.

---

### Post by lbmounse on 2006-04-04
When I eventually upgrade to dapper, will i have to upgrade to Breezy first?

---

### Post by az on 2006-04-04
[QUOTE=lbmounse]I'm also running breezy on an 850 MHz, 256 MB laptop, and it doesn't seem too slow.[/QUOTE]

I have found the threshold to be around a 500 Mhz pentium (not a Celeron -they have no cache!)

Anything faster than a 500Mhz Pentium will give you a decently responsive desktop.  Heavier tasks like video or multimedia apps are not as friendly, but for basic computer tasks, it's fine.  Below about 300 MHz, it becomes painful.

But honestly, a 2 GHz computer's Ubuntu desktop is not that much more responsive than a 500Mhz one...

---

### Post by lbmounse on 2006-04-05
That could be a problem with the destop, for it has a celeron.

---

