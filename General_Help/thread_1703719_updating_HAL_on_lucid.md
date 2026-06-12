---
title: "updating HAL on lucid"
date: 2011-03-09
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-03-09
i was looking at the requirements for firefox 4
[http://www.mozilla.com/en-US/firefox/system-requirements.html](http://www.mozilla.com/en-US/firefox/system-requirements.html)
lucid comes with HAL 0.8.14
is there a ppa or deb file for HAL

---

### Post by 3Miro on 2011-03-09
> **pqwoerituytrueiwoq said:**
> i was looking at the requirements for firefox 4
[http://www.mozilla.com/en-US/firefox/system-requirements.html](http://www.mozilla.com/en-US/firefox/system-requirements.html)
lucid comes with HAL 0.8.14
is there a ppa or deb file for HAL

"HAL 0.5.8 or higher", you have 0.8.14, so you should be fine. I don't know what functionality they get from HAL, it is deprecated, so I doubt it is a really useful feature.

---

### Post by pqwoerituytrueiwoq on 2011-03-09
[IMG]http://warcraft.ingame.de/forum/images/smilies/facepalm.gif[/IMG]

---

### Post by lithopsian on 2011-03-09
Hal only goes up to 0.5.14.  This is the release in every Ubuntu from Lucid onwards, subject to minor security tweaks, and it will never get any higher.

Firefox doesn't need Hal at all and runs just fine without it, just like it can be run with Network Manager or Gnome, assuming you have something equivalent in place.  I don't actually know what Firefox uses Hal for.

There are actually a great deal more requirements than listed on that page but they are considered such integral parts of any Linux distro that they aren't stated.  libc6 for example.  There are also some tricky dependencies like libstdc++ which may end up getting listed.

---

