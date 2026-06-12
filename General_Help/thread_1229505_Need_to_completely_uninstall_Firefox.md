---
title: "Need to completely uninstall Firefox"
date: 2009-08-02
forum: General Help
---

### Post by kg84 on 2009-08-02
Following on from my thread earlier today (re. Tiger) in the security section of the forum, I now find myself in a bit of a pickle.

I need to uninstall Firefox and do a nice fresh re-install. However it seems I have traces of FF in a number of folders (including many hidden). I have attempted to get rid of what i could find, but subsequent re-installations have failed, I think to the remnants of certain files still existing.

Is there a single command I can run that will seek out and remove all files/folders related to Firefox so that I can do a nice clean, fresh re-install?

I fear that if I dont clear all left over bits of FF that I will not be able to get it running again with a fresh install.

Cheers.

---

### Post by kg84 on 2009-08-02
I got it sorted.

I initially tried a fresh install through ubuntuzilla, but this failed each time, stating access to a particular folder (for profile?) was denied.

I got rid of everything FF related via synaptic and then did a fresh install with ubuntuzilla.

All is now well :)

---

### Post by nanotube on 2009-08-02
glad it worked out :)
for your future reference, the firefox profile is stored in the ".mozilla" directory in your home dir. if it ever gives you trouble again, just run
```
sudo mv ~/.mozilla ~/.mozilla.backup
```
to get it out of the way.

---

