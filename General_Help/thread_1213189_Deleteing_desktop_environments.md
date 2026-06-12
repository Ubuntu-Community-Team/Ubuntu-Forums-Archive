---
title: "Deleteing desktop environments"
date: 2009-07-14
forum: General Help
---

### Post by emacbri on 2009-07-14
Hi,

I wanted to test out the KDE and Xfce desktop environments to see how they stood up to Gnome, so I installed the Kubuntu and Xubuntu desktop packages. Now when I try to un-install them, all the other packages that were associated with these packages remain. I would go through them and un-install them one by one, but it would take too long, and I don't know what packages to delete anyway. Any help would be appreciated...

---

### Post by schmidtbag on 2009-07-14
you could try installing gtkorphan which removes packages that are no longer dependant upon anything, but dont' expect that to fully work

---

### Post by CatKiller on 2009-07-14
Depending on how you installed the kubuntu-desktop and xubuntu-desktop packages*, the dependent packages that got installed will have been marked as "automatically installed." They'll show up as such in Synaptic, or ```
sudo apt-get autoclean
``` will remove them.

*AFAIK this is now the default behaviour for Synaptic, aptitude and apt-get, but there is the possibility that this didn't happen for you for some reason.

---

