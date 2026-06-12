---
title: "ubuntu 10.04 skips grub menu after update"
date: 2010-04-14
forum: General Help
---

### Post by rmkscrambler on 2010-04-14
I have been using ubuntu 64bit for a couple months I went a head and upgraded to 10.04 beta and every thing worked fine for about two weeks I do dull boot with vista. Recently  I ran update manager and it updated the kernel to 2.6.32-20 along grub and other stuff. Now the grub menu never shows during boot. So I have no way to load my windows partition.
I have tried holding shift during boot and even esc neither works shift seams to slow the boot down but the menu never appears.
Don't know if this is a bug or just a setting I need to change.

---

### Post by ed-koala on 2010-04-14
You can fix by editing /etc/default/grub and changing the line GRUB_HIDDEN_TIMEOUT=0 so it reads # GRUB_HIDDEN_TIMEOUT=0

Grub will now show for 10 secs before auto booting into default OS.

---

### Post by rmkscrambler on 2010-04-15
Thanks thats the file I needed I was playing with the grub.cfg file and didn't want to change anything in their

---

