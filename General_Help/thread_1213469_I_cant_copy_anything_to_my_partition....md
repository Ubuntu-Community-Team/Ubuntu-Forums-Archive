---
title: "I cant copy anything to my partition..."
date: 2009-07-14
forum: General Help
---

### Post by Darkoblivion2 on 2009-07-14
hi all...

ok so, i have a western digital 1TB hdd.

when i installed jaunty i allocated 500gb for my root partition(ext3), 25bg for swap, and 475gb for free space(ext3)...

but now i cant copy anything to that free space... and when i right click in that free space partition, i cant create new folder...

what should i do in gparted to fix this?

ps... ubuntu is the ONLY os i have installed, no dual booting here...

---

### Post by merlinus on 2009-07-14
```
gksudo nautilus
```

Navigate to the partition mountpoint, rightclick, properties, permissions.

---

### Post by Darkoblivion2 on 2009-07-14
that did it! tyvm!

---

