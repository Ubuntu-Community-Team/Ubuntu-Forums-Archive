---
title: "Uninstalling calibre"
date: 2009-11-05
forum: General Help
---

### Post by Trinexx on 2009-11-05
I recently installed Calibre on my system to manage my vast ebook library, but I didn't particularly like it, so now I'm attempting to uninstall it. However, when I try running the uninstall script, it errors out on me.

trinexx@aleph:~/ebooks/calibre$ sudo calibre-uninstall
Invalid invocation of calibre loader. CALIBRE_CX_EXE not set

Support for this program is far and few in-between, so I was hoping someone here could help me. Any ideas?

---

### Post by Giblet5 on 2009-11-05
The calibre uninstall script is obviously broken.

Welcome to the age of Before Sophisticated Package Management!

Any time you install something on Ubuntu without using Synaptic, aptitude, adept, or some other package manager, then you run the risk of not being able to remove it.

How big is calibre? If it's a few megabytes and you're not critically low on disk space, just leave it installed and don't use it.

If it's just plain gotta go, then read through the supplied uninstall script and do what it would do if it worked.

Not being snarky at all: those really are your only options.

---

### Post by Trinexx on 2009-11-05
I figured as much, thought I would make sure before I go mucking around in places I don't understand. I'll just remove the obvious signs of its presence and leave everything else alone.

Thanks.

---

### Post by mediax on 2009-11-12
Alternatively, you could try contacting the creator, either by way of the link to his web site in Calibre, or via the Calibre forum at MobileRead.com (he's a regular contributor and very helpful).

---

### Post by elementalvoid on 2009-11-16
If you look at calibre-uninstall you'll notice that it is just python code.

I used the following:
```
sudo python /usr/bin/calibre-uninstall
sudo rm -rf /opt/calibre
```

---

### Post by jonthysell on 2010-05-07
> **elementalvoid said:**
> If you look at calibre-uninstall you'll notice that it is just python code.

I used the following:
```
sudo python /usr/bin/calibre-uninstall
sudo rm -rf /opt/calibre
```

Thanks a bundle. Next time, no more "custom" install apps. Sticking to the package manager.

---

