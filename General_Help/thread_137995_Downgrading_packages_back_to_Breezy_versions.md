---
title: "Downgrading packages back to Breezy versions?"
date: 2006-03-01
forum: General Help
---

### Post by Zeroangel on 2006-03-01
Hey all, I seem to have messed up a bit.

I enabled the dapper repositories to update a package and by some stroke of idiocy I forgot to disable it, so when the update manager told me that updates were ready a clicked install. And then realizing I was upgrading Breezy -> Dapper I canceled about after about 10 packages were installed. So now i'm getting crashes with evolution among other things. 

I looked in Synaptic and marking certain packages for uninstall makes them want to take everything with them (gnome-desktop, gdm, nautilus, etc). 

So my question is, is there a way to force downgrade these packages without having them take several other packages down with them?

---

### Post by CodyJarrett on 2006-04-26
i have sort of the same problem. I had to install some newer packages manually, but now Evolution crashes when formatting messages. Is there no way to fix these problems?

---

### Post by Ramses de Norre on 2006-04-26
Maybe you can change your repo's back to breezy and run sudo apt-get update && sudo apt-get dist-upgrade.

---

