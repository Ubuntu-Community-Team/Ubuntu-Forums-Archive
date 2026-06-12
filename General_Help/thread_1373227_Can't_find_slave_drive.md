---
title: "Can't find slave drive"
date: 2010-01-05
forum: General Help
---

### Post by plentymoon on 2010-01-05
I can't find my slave hardrive I went and checked to see if I forgot to plug it in but I i had everything in the correct places I'm thinking it might be a defected drive. any help at all?

---

### Post by oldfred on 2010-01-05
Does the BIOS see it?  When you say slave I assume you mean an older IDE or Pata drive. Are you using 40 wire cable with the connectors all the same color, if so the jumpers must be set correctly on the drive. If the newer 80 wire cable for cable select - 3 different color connectors then the jumper on the drive must be cable select.

---

### Post by SecretCode on 2010-01-05
When you say you can't see it ... does it not show up in 
```
ls -l /dev/disk/by-path
```

---

