---
title: "When you un-install a program"
date: 2011-07-24
forum: General Help
---

### Post by Spae on 2011-07-24
Is all data related to it removed?

I just remember once un-installing firefox then re-installing later to find i still had my add-ons.

But I'm asking this more of a general question not just to do with firefox.

I have found folders from programs I have un-installed in the 'etc' directory but I can't delete things from there?

---

### Post by CatKiller on 2011-07-24
> **Spae said:**
> Is all data related to it removed?

No. Nothing is removed from a user's Home directory.

> I have found folders from programs I have un-installed in the 'etc' directory but I can't delete things from there?

To remove the system-wide configuration files you need to purge rather than remove.

A user cannot change anything outside their Home folder. To change things outside your Home folder you need to temporarily become root with *sudo*. There is a great deal of instruction about this process.

---

### Post by oldos2er on 2011-07-24
Sorry, OP, apparently there is no way to do this other than manually deleting the config files in your home folder.

---

### Post by Jamesi on 2011-07-24
thank you for telling us :p

---

### Post by CatKiller on 2011-07-24
> **oldos2er said:**
> In Synaptic check 'Completely remove' to uninstall config files in your home folder. To do the same thing with apt-get, run **sudo apt-get purge <program>**

Purge doesn't remove config files from the Home folder.

---

### Post by oldos2er on 2011-07-24
It's --purge remove, isn't it?

Never mind, I found the answer. Thank you for correcting me. I could've sworn that there was some option for either dpkg or aptitude to remove a user's config files, but I was mistaken. The man page for apt-get purge says 'purge is identical to remove except that packages are removed and purged (any configuration files are deleted       too).' I'd assumed *any* really meant *any*.

---

