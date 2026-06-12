---
title: "mdadm not reporting disk errors"
date: 2010-03-31
forum: General Help
---

### Post by mcfang on 2010-03-31
I have mdadm setup to monitor and report on errors and it works as expected for major conditions, eg. I get an email when a drive fails.

But recently I discovered a disk in a RAID1 array had been having serious errors that were causing performance problems and probably leading towards a complete failure.

Can mdadm monitor and report on conditions such as these (the following logs were repeated hundreds of times)?
```

Mar 31 18:52:55 lapis kernel: [503556.909346] sd 0:0:0:0: [sda] Unhandled sense code
Mar 31 18:52:55 lapis kernel: [503556.909349] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 31 18:52:55 lapis kernel: [503556.909353] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Mar 31 18:52:55 lapis kernel: [503556.909359] Descriptor sense data with sense descriptors (in hex):
Mar 31 18:52:55 lapis kernel: [503556.909362]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
Mar 31 18:52:55 lapis kernel: [503556.909372]         0d f8 ff 1c
Mar 31 18:52:55 lapis kernel: [503556.909376] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Mar 31 18:52:55 lapis kernel: [503556.909394] ata1: EH complete
Mar 31 18:52:55 kernel: [503556.914730] raid1:md2: read error corrected (8 sectors at 234421976 on sda1)

```

---

