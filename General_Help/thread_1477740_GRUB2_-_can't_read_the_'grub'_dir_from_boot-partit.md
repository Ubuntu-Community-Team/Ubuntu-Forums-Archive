---
title: "GRUB2 - can't read the 'grub' dir from /boot-partition at a cold start"
date: 2010-05-09
forum: General Help
---

### Post by udedok on 2010-05-09
There are two HDDs installed: "first" and "second".

The 9.10 is installed on the first (with /boot in the / partition). The 10.04 was installed (from scratch) on the second with /boot as separate partition. There is grub 1.5 on the first's MBR & grub2 on the second's MBR.

I have the problem:
- After a cold start and choosing the second form BIOS-boot menu, I am get:
```
grub error: out of disk. grub error: out of disk.
grub rescue>
```'ls /' lists content of the /boot; it contains the 'grub' dir
'ls /grub' gives 'error: out of disk'

- After the 9.10 starts from the first, GRUB2 normally starts on the second - i.e. it can read /boot/grub...

Are there some considerations?

---

