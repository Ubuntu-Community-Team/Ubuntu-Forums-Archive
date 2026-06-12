---
title: "Encrypted ext3 partition ( TrueCrypt ) - fsck error."
date: 2009-07-29
forum: General Help
---

### Post by credobyte on 2009-07-29
I've made an encrypted partition with [COLOR=Blue]TrueCrypt[/COLOR] and on every boot I get fsck error ( can't detect filesystem or smth like that ).
The question is - how do I get rid of this error ( eg. "hide" it ) ? Every time when this error comes up, I need to press [COLOR=Blue]Ctrl + D[/COLOR], which is .. annoying !

```
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03c0aeef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1094     8787523+  83  Linux
/dev/sda2            3527        9733    49857727+   5  Extended
/dev/sda3            1095        3526    19535040   83  Linux
/dev/sda5            9609        9733     1003968   82  Linux swap / Solaris
[COLOR=Red]/dev/sda6            3527        9608    48853602   83  Linux[/COLOR]

Partition table entries are not in disk order

Disk /dev/sdb: 1017 MB, 1017117696 bytes
255 heads, 63 sectors/track, 123 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x801fda4f

```

---

