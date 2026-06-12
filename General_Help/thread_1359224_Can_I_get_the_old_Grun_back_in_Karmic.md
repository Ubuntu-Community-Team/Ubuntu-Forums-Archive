---
title: "Can I get the old Grun back in Karmic?"
date: 2009-12-19
forum: General Help
---

### Post by Hyper Tails on 2009-12-19
I was wondering if I can get the old Grub back that use to be on jaunty on karmic

I want to use kgrubeditor to edit the current grub menu but i cant because it says grab menu not found.

many help[ will be appreciated

PS: i have synaptic package manager installed

---

### Post by lightstream on 2009-12-19
I for one don't know what you're talking about - at least my grub files all seem to still be the same and I upgraded from Jaunty to Koala. 

Certainly the menu.lst file is in the same place, and seems laid out pretty much the same.

---

### Post by oldos2er on 2009-12-19
If you upgraded to 9.10, you're still using grub legacy.

 It's possible to remove grub2 and install grub legacy, but in my opinion it's best to learn grub2. It's my understanding grub legacy is no longer in development.

---

### Post by Hyper Tails on 2009-12-19
do you know how i can get kgub editor in karmic?

just asking

---

### Post by Leppie on 2009-12-19
you can download it [here]("http://www.kde-apps.org/content/show.php?content=75442") and install it, but it's my understanding that it only supports menu.lst where grub2 uses grub.cfg.
you could always copy menu.lst to grub.cfg if you wish.

---

### Post by oldos2er on 2009-12-19
kgrubeditor is not in Karmic's repositories, for obvious reasons. But you can find it here: [http://packages.ubuntu.com/search?searchon=sourcenames&keywords=kgrubeditor](http://packages.ubuntu.com/search?searchon=sourcenames&keywords=kgrubeditor)

---

