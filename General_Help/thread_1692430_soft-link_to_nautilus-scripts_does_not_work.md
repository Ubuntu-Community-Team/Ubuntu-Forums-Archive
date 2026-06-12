---
title: "soft-link to nautilus-scripts does not work"
date: 2011-02-21
forum: General Help
---

### Post by sa-mejia on 2011-02-21
I would like to have all of my nautilus scripts under a directory in Dropbox, and link all of my computers to such a directory.  

I tried to link my computer to this folder, by replacing the nautilus-script folder for a soft link.

rm ~/.gnome2/nautilus-scripts
ln -s ~/Dropbox/NautilusSriptDropbox ~/.gnome2/nautilus-scripts

However, this soft link behaves strangely.  When I click on it from Nautilus, nothing shows up (even though if I go to it in the terminal, it goes exactly where it has to go and shows all the files I have in my Dropbox file).  

The main problem is that because this soft link does not work... it will not see any of my files under my Dropbox folder, and therefore I have no way of syncing my nautilus scripts with my Dropbox directory.

Why is this happening?  How could I solve it?  

S.

---

### Post by sa-mejia on 2011-02-22
bump

---

### Post by sa-mejia on 2011-03-02
re-bump?

---

