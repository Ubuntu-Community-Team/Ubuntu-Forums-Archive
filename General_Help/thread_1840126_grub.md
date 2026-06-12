---
title: "grub"
date: 2011-09-07
forum: General Help
---

### Post by mr.farenheit on 2011-09-07
how do i go about getting the grub menu to show when booting up?

---

### Post by Quackers on 2011-09-07
If you only have one operating system installed the default behaviour is that the grub menu does not show.
If you tap the shift key (or the Esc key) during boot the menu should show.

---

### Post by claracc on 2011-09-07
I suppose you have grub2.

In /etc/default/grub you coment with # the line starting GRUB_HIDDEN_TIMEOUT=
Then you have to have a positive integer (5, 10, 15, ..) in the line GRUB_TIMEOUT=

Then tou have to run sudo update-grub in console.

---

### Post by mr.farenheit on 2011-09-12
thanks much

---

