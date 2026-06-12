---
title: "mkImage problems on Arm system"
date: 2012-01-15
forum: General Help
---

### Post by RichardUK on 2012-01-15
I have 11.04 running on my Panda board and I'm trying to change the boot args.

I have a txt file that has the boot args in it and create a new boot.scr script for uBoot with the following command.

```
mkimage -A arm -T script -O linux -C none -a 0 -e 0 -n "boot.scr" -d boot.scr.txt boot.scr
```

I run this on my x86 Ubuntu 11.04 dev system.

But when I boot the panda board I get the following errors, any ideas?


```
reading boot.scr

309 bytes read
Running bootscript from mmc0 ...
## Executing script at 82000000
reading uInitrd

3983187 bytes read
Wrong Image Format for bootm command
ERROR: can't get kernel image!

```

The script is almost identical as the one that works with just as small change. I even tried it without the change and it still fails.

---

