---
title: "Using apt-get to download packages to USB drive?"
date: 2009-11-05
forum: General Help
---

### Post by madchine on 2009-11-05
I need to download the build-essentials packages to transfer them to a laptop which does not - as yet - have internet access.  Getting synaptic to generate a script simply results in downloading the pseudo-package.

I must have done this a thousand times in Arch using pacman, but apt-get is proving a royal pain in the neck in this regard. Any ideas?

---

### Post by mikewhatever on 2009-11-05
Actually, it shouldn't be very hard:

```
sudo apt-get -d install build-essential
```

Then grab it from /var/cache/apt/archives; -d makes sure the package + dependencies are downloaded only.

---

