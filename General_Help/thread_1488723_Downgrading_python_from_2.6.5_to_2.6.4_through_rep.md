---
title: "Downgrading python from 2.6.5 to 2.6.4 through repository?"
date: 2010-05-20
forum: General Help
---

### Post by supergrover1981 on 2010-05-20
Hi folks,

I need to downgrade my version of python from 2.6.5 to 2.6.4. I'm running Lucid 64 and ideally I'd like to keep a repository install of Python. I've never really messed with repositories beyond basic installs/removes/updates.

So, is it possible to downgrade to a minor sub-version in the repository - and if so, any suggestions how?

Cheers...

---

### Post by dino99 on 2010-05-20
[http://packages.ubuntu.com/karmic/python/](http://packages.ubuntu.com/karmic/python/)

you can force this package into synaptic menu (change the sources.list with "karmic", update, force the package, then change back your sources.list and update again)

be aware you might have some conflicts when downgrading, have to try to know what happen

---

