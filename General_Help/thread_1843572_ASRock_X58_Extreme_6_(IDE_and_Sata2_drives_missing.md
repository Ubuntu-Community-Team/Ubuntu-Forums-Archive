---
title: "ASRock X58 Extreme 6 (IDE and Sata2 drives missing)"
date: 2011-09-13
forum: General Help
---

### Post by Simi23 on 2011-09-13
I just got this awesome MB ASRock X58 Extreme 6 and turn out there is no support for Sata2 and IDE controllers. All drives in Sata3 show up fine but if I plug them in to Sata2 they not showing up in system. I have Ubuntu 10.10 and also tried 11.04.
Funny thing is I can boot from HDD if I plug it in to Sata2 and then it show in system but only then, did anybody had same problem?
Thank you

---

### Post by 3Miro on 2011-09-13
Just a guess:

I have a Gigabyte mobo, but it has an option to switch between "ahci and ide". IDE seems limited and once I put 4 disks in, it started giving me trouble. I had to enable "IDE to AHCI" from the BIOS. It was in preferentials or advanced chipset settings.

---

### Post by Simi23 on 2011-09-14
Thank you 3Miro that did it, now all Sata III and II are working fine ;-) old IDE (pata) port still doesn't work but I'm not worried too much about that, I only had one old drive there anyway.

---

