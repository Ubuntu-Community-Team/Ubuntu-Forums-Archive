---
title: "Uninstalling applications leave &quot;junk&quot; files somewhere"
date: 2006-02-09
forum: General Help
---

### Post by Tyltyl on 2006-02-09
Hello,
yesterday I installed the game Ur-Quan Masters from the repositories and then I copied some remixed music packs into the game folder.
After I uninstalled though I noticed that I lost like 150+MB in HD space. I cleaned everything, I did an apt-get clean, cleaned orphaned libraries and followed a wiki to cleanup Ubuntu but nothing.
It's the second time that this happens to me, looks like big applications tend to eat up my HD space with litter. Where and how can I find it? I looked into /home, /tmp, /var etc. but I don't see anything remaining from the game.
Thanks if you can give me a tip :)

---

### Post by Zalbor on 2006-02-09
Sorry if I'm no help, but when you uninstalled them, did you choose "remove package" or "completely remove package" (that's assuming you used synaptic, I don't know the difference in commands)?

---

### Post by Tyltyl on 2006-02-09
Yes I did already :( That's why I have no idea where I'm wasting space...

---

### Post by Tyltyl on 2006-02-09
Any idea?

---

### Post by snowjunkie on 2006-02-09
[QUOTE=Tyltyl]Any idea?[/QUOTE]
I'm not at my machine, but would running an apt-get autoclean, or apt-get clean help things?  Check the commands first as I'm not sure if that is correct.

---

### Post by emperor on 2006-02-09
You can use Synaptics to remove the configuration files, scripts and other "litter", Look in the "Status" window list.

---

### Post by Tyltyl on 2006-02-09
[QUOTE=emperor]You can use Synaptics to remove the configuration files, scripts and other "litter", Look in the "Status" window list.[/QUOTE]

There's nothing to clean out :(
This is the strangest thing, apparently I already removed everything I installed, but it didn't clean out the space occupied by the game/application

---

### Post by Tyltyl on 2006-02-10
So just to let you know, I solved.

I deleted some big packages with sudo nautilus, and they remained in the root trash.
Stupid me...

---

