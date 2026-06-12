---
title: "boot freezes at device-mapper: dm-raid45: initalized"
date: 2011-09-26
forum: General Help
---

### Post by iconoclast hero on 2011-09-26
10.10 / 2.6.35-30 and 2.6.35-28 but NOT 2.6.35-22

Thought it might have had something to do with a line in fstab mounting a NFS share but I commented that out and it still freezes.  I am at a loss to figure out the next step.  Is it possible that this dm-raid45 could have gotten corrupted?  control-alt-delete allows for a reboot but can't figure out the next step.

The full list of messages on the screen where the boot freezes is
```

[#1]  xor: automatically using best check summing function: pIII_sse
[#2]  pIII_sse: 6716.000 MB/sec
[#3]  xor: using function: pIII_sse (6717.000 MB/sec)
[#4]  device-mapper: dm-raid45: initalized v0.2594b

```

---

