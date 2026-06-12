---
title: "Power Outage"
date: 2010-05-30
forum: General Help
---

### Post by jjjjjjj9175@ on 2010-05-30
I was working on my backup computer, which has ubuntu 9.10, and I had a power outage.  When my power came back on I tried to boot up my computer. GRUB loaded correctly but when I tried to boot into ubuntu all I got was a black screen.  I left my computer on for about 30 minutes to see if it would go off but that didn't work.  Does anybody know whats wrong and how can I fix it?

---

### Post by CharlesA on 2010-05-30
Try booting into recovery mode and see what happens.

---

### Post by jjjjjjj9175@ on 2010-05-31
I tried booting into recovery mode and it didnt do anything

---

### Post by WinRiddance on 2010-05-31
See if you can at least see your files with a LiveCD. If they're there do a search for rebuilding grub or just back up your existing home/user data followed by reinstalling Ubuntu?

---

### Post by Dejavou42 on 2010-05-31
Boot from the Install CD, open a terminal, type "sudo fdisk -l", and run fsck on your partitions.

---

