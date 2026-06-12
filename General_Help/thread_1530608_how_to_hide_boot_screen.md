---
title: "how to hide boot screen?"
date: 2010-07-13
forum: General Help
---

### Post by WinterMadness on 2010-07-13
you know that screen that says ubuntu and has the progress bar under it before you log in?

I would prefer just text.

---

### Post by Twitch6000 on 2010-07-13
In order to make it just text you need to remove plymouth.

sudo apt-get remove plymouth -f should do the trick.

---

