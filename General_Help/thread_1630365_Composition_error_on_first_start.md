---
title: "Composition error on first start"
date: 2010-11-25
forum: General Help
---

### Post by Bear-Lt on 2010-11-25
After boot, first time I log on to Gnome I get compositing error (Docky shows one in top right corner) "Docky requires compositing to work properly. Please enable compositing, and restart Docky.". Furthermore some black wide stripe appears in the bottom of the screen, mouse pointer looks like a black cross and window decoration are missing. If I log off and re-log on everything works like a charm.
After first boot:
[IMG]http://img41.imageshack.us/img41/3727/screenshothtj.png[/IMG]
After re-log on:
[IMG]http://img684.imageshack.us/img684/5967/screenshot1kfz.png[/IMG]
Ubuntu 10.10 on Acer Aspire One (A110L) with Compiz enabled and Docky installed.

Is there a way to fix it?

---

### Post by golzuam on 2010-11-25
I'm having the same problems. The quick fix is to enable desktop effects through the appearance menu option. Metacity also crashes, I have to do a metacity --replace (or emerald --replace) to see the menubars in my gnome windows.

---

### Post by Bear-Lt on 2010-11-28
News:
I've noticed, that this glitch appears every second boot.

Boot &#8211; glitch appears
Relogon - no glitch
Relogon - glitch appears
Relogon - no glitch

And it isn't affected (as I suspect) by external monitor I use. I get that glitch using external monitor and without it. Any ideas? Maybe it's because of updated grub settings (I've made some corrections in config file so that I could see boot splash image, that disappeared right after installing Ubuntu 10.10)?

---

