---
title: "Ubuntu disappeared from the menu!"
date: 2012-10-01
forum: General Help
---

### Post by OllieGab on 2012-10-01
I've been running Ubuntu 12.04, Debian 6 and Windows on the same machine without any problems. I use Ubuntu & Debian in equal measurements but suddenly, for no apparent reason (ie I was not doing any tweaking or experimenting) the Ubuntu entry on the grub menu has gone. 
The 'active' grub is the one in Ubuntu but since I can't boot Ubuntu now, how do I fix that?
I tried to update grub from within Debian but only W and Debian were discovered.

Cheers

---

### Post by GreatDanton on 2012-10-01
Have you tried[ boot-repair]("https://help.ubuntu.com/community/Boot-Repair")?

Regards.

---

### Post by OllieGab on 2012-10-02
Strangely enough it seems to have sorted itself out! I did another 'update-grub' from within Debian, which brought the Ubuntu entries back - witch a vengeance! About 10 different entries instead of the original two. But I don't mind; the main thing is that they are back!
Have no idea why it happened!
Would be interesting to know, though, if its now the Debian grub that is active (Debian is now the first entry on the list) or the Ubuntumone.

---

