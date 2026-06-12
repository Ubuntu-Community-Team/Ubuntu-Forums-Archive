---
title: "[package] ubuntu-desktop - safe to remove?"
date: 2004-10-25
forum: General Help
---

### Post by goDez on 2004-10-25
Hi!

I'm so far greatly enjoying Ubuntu linux (the Warty Warthog edition, ofcourse).
I just don't like certain programs. For instance, rhytmbox is already replaced with xmms. Also the mediaplayer... It doesnt seem to play any files :S So, I asked a friend of mine, and he told me to install Mplayer. I can't find any such program in the default packages. I'll figure it out with google etc, though.

Anyway, now for the real problem.. I tried to remove rhytmbox (since I don't use it) but then it asks me if I want to remove the package ubuntu-desktop as well (since its a part of that package, probably). There are also a number of other packages requiring me to also delete the package ubuntu-desktop.

Q: Is this safe? Or will everything just stop working? :S

/me is just very cautious about his freshly installed system and wishes to keep it working :)

Thanks in advance.

---

### Post by jdong on 2004-10-25
ubuntu-desktop is a metapackage (err, translate term from Gentoo-ese) , it's just an empty package with a bunch of dependencies, just like gnome or kde (they are empty, but depend on nautilus, konq, the libs, etc etc etc).


In short, yes, it's safe to remove ubuntu-desktop. Nothing will be lost.

---

### Post by goDez on 2004-10-25
thanks alot!

---

