---
title: "no menu entry or icon after CLI install of vim-full"
date: 2009-08-20
forum: General Help
---

### Post by Ascenti0n on 2009-08-20
can someone tell me why there wasn't a menu entry and icon created for vim/gvim, after installing from the command line:

```
sudo apt-get install vim-full
```

More importantly, how do I install/configure the missing items.

incidentaly: I did check the 'system>preferences>main menu' option to see if it was there but just not checked. It wasn't there.

---

### Post by Raffles10 on 2009-08-20
I think the package you want is:

```
sudo apt-get install vim-gnome
```

vim-full is simply a transitional package from vim-full to vim-gnome.

---

### Post by Ascenti0n on 2009-08-20
> **Raffles10 said:**
> I think the package you want is:

vim-full is simply a transitional package from vim-full to vim-gnome.

I hadn't heard that one before. However, no need to run your suggested command as, for some reason, after restarting my machine, both appeared in the menu stack as expected.

Thanks

---

