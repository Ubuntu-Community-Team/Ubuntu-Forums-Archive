---
title: "Force libasound downgrade"
date: 2012-01-29
forum: General Help
---

### Post by J V on 2012-01-29
I upgraded libasound2 to accommodate a program that didn't cooperate after all. This left me with a PPA version of libasound2 and now that I need the old version, I can't install it.

Force version has no effect and if I remove it altogether and install manually later half my system goes with it.

How do I force downgrade to the stock repository version when synaptic isn't cooperating?

**To any future viewers** the command for installing a specific version is:
```
sudo apt-get install package=version
```

Easy as that :)

---

