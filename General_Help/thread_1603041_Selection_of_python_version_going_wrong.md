---
title: "Selection of python version going wrong"
date: 2010-10-22
forum: General Help
---

### Post by dathui on 2010-10-22
I'm trying to install python-crypto to my python2.6, but when I run apt-get install python-crypto it says:

INFO: using unknown version '/usr/bin/python2.7' (debian_defaults not up-to-date?)

But I've looked in /usr/share/python/debian_defaults and there isn't any mention of 2.7 there, should have been removed when I uninstalled python2.7 earlier. Where else could it be looking? Or is debian_defaults only read once per boot or something?

---

