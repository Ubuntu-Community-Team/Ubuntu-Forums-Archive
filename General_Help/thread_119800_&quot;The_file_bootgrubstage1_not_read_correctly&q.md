---
title: "&quot;The file /boot/grub/stage1 not read correctly&quot;"
date: 2006-01-20
forum: General Help
---

### Post by gumbald on 2006-01-20
Strange problem, can't find one like it...

I had ubuntu installed on my 2nd PC, working fine, but was then given an 80gb drive, so decided to install XP also, and use a dual boot. I configured it with the 80 as the master, and 17 as the slave, and both had their OS installed and working fine. The problem came when I tried to install GRUB in order to choose between them. On going into rescue mode and typing "grub-install /dev/hda" it gives the error message:

"The file /boot/grub/stage1 not read correctly"

and returns me to the prompt. To attack this from another method, I tried physically changing my drives around and simply edited my existing GRUB file, however when I chose Windows, it got no further than the "chainloader" line.

Can anybody point me in the right direction? My current method of dual booting is to unplug a molex!

---

### Post by gumbald on 2006-01-20
Just tried the live CD method, got the same error.

Any ideas what this means? :)

---

