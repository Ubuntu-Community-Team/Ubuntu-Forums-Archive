---
title: "Did the software get removed?  Depends."
date: 2009-12-18
forum: General Help
---

### Post by Shibblet on 2009-12-18
When you pick a software package from Synaptic, it sometimes installs dependencies in order to get the software to work.

But does it uninstall those dependencies when the package is removed?  If not, why?

---

### Post by abyrne on 2009-12-18
No. but you can remove any unneeded packages by running

```
sudo apt-get autoremove
```

---

### Post by Shibblet on 2009-12-18
> **abyrne said:**
> No. but you can remove any unneeded packages by running

```
sudo apt-get autoremove
```

So, apt will know which dependencies are not being used and remove them for you?  That's awesome.  I guess I need to learn more about apt.  LOL

I flippin' love Ubuntu.

---

### Post by deathbyswiftwind on 2009-12-18
yep ubuntu is pretty sweet ;) Im guessing it doesnt autoremove them so you dont have to redownload and install them later if needed.

---

