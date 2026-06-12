---
title: "re-partitioning"
date: 2009-07-29
forum: General Help
---

### Post by scrambledarthur on 2009-07-29
I messed up the partitioning of my drive pretty hard, but it's okay.

Since the windows partition of my drive is pretty much useless, how can I make it so that my whole hard drive is available for Ubuntu?

---

### Post by merlinus on 2009-07-29
Is ubuntu already installed?  If not, choose use entire disk whilst installing.

If so, then you can use gparted to add the freed-up space from windows to your ubuntu partition, or format it as ext3 and use it for storage (docs, music, photos,and the like).

If you decide to go this route, then you will have to add an entry in /etc/fstab so it mounts automatically.

Post back if you need further assistance or clarification.

---

### Post by scrambledarthur on 2009-07-29
Much Thanks

---

### Post by scrambledarthur on 2009-07-29
Okay, I downloaded the program and have it up. How do I know which is the one ubuntu is using and which one is the one that I should cannibalize?

---

