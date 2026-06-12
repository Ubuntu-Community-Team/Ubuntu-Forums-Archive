---
title: "read/write access via SSH on a new mount point??"
date: 2009-07-14
forum: General Help
---

### Post by jespes on 2009-07-14
Hello,

question about a mount point for a USB drive: I've successfully created a mount point in my account's "home" folder, but when I try to access the disk via SSH, sometimes it doesn't give me read/write permissions. (Sometimes it does.) 

How can I make it so that I always have read/write permissions on that disk, via SSH, via the mount point in the "home" folder?


Many thanks,
JP

---

### Post by jespes on 2009-07-15
bump.
  tia for advice on it...

---

### Post by jespes on 2009-07-15
bump

looking for help on getting permanent read/write access to a USB drive accessed via SSH. thanks!

---

### Post by jespes on 2009-07-20
bump.

---

### Post by hetx on 2009-07-20
Although enabling the root account is generally frowned upon, SSH log in as root would give you permission. But that seems like just curing the symptoms instead of the disease.

---

### Post by jespes on 2009-07-20
thanks and yeah, i dont want to ssh in as root....

I'm wondering if  there are terminal commands by which, when I manually mount the external HDD (or when I create its mount point, or both), I can also manually assign it some kind of overall read/write access.

but i'm a noob, so i am a bit over my head with terminal stuff like that.

---

