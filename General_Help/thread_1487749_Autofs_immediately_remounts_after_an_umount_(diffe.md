---
title: "Autofs immediately remounts after an umount (difference 64 bit and 32 bit)"
date: 2010-05-19
forum: General Help
---

### Post by foobar66 on 2010-05-19
I've got a laptop and netbook. Both running Lucid. Laptop runs x64, netbook runs x86.

Both PC have an autofs mount for a Windows partition.

On the laptop (64 bit):
Mount works fine => after 5 min timout, partition get unmounted => OK.

On the netbook (32 bit)
Mount works fine => after 5 min timeout, partition gets unmounted => BUT partition immediately remounts again.

I have checked with lsof/fuser and no process is using the partition.

Therefore, I do not understand why on the netbook (32 bit) the partition immediately remounts after the 5 minute timeout and unmount.

Any help?

---

