---
title: "Delete 1 os from os-prober while leaving other alone"
date: 2010-05-31
forum: General Help
---

### Post by iamsickofschool on 2010-05-31
Sorry if this has already been posted but I can't seem to find an answer anywhere.

I have an OS (the backup partition for Windows 7) that I want to get rid of in grub2 and it is located in /etc/grub.d/os-prober
However, Windows 7 is also located in os-prober so I can't just delete/disable os-prober all together. Is there a way to get rid of the backup on the grub list without actually deleting the partition?

the only reason I want it removed is that if you go into the backup partition is that it deletes grub2 and the computer fails to boot into any OS afterwords, and I really don't want to have to download grub2 over again if I accidently hit the backup partition.

Any help is appreciated

---

### Post by sisco311 on 2010-05-31
Hi and welcome to the forums!

See: [thread=1287602]Grub 2 (Title) Tweaks[/thread] #4. Hiding the Windows Recovery Partition

---

