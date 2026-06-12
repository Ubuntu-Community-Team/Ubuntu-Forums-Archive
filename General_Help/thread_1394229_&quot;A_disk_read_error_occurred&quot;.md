---
title: "&quot;A disk read error occurred&quot;"
date: 2010-01-30
forum: General Help
---

### Post by Hallvor on 2010-01-30
I bought a netbook and tried setting up a dual boot. Shrinked the Windows partition to 20 GB and used the rest for GNU/Linux.

GNU/Linux boots just fine, but now Windows. Here is what I get: 

```
Booting 'windows'

rootnoverify (hd0,1)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

A disk read error occurred
Press Ctrl+Alt+Del to restart
```

I did not test if Windows worked after I shrinked it, but I was able to run a system recovery with no errors just in case there was any corruption.

Here is the output of fdisk -l: 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         764     6136798+  12  Compaq diagnostics
/dev/sdb2             765        3240    19888470    7  HPFS/NTFS
/dev/sdb3            3241       19457   130263052+   5  Extended
/dev/sdb5            3241        3514     2200873+  82  Linux swap / Solaris
/dev/sdb6            3515        6112    20868403+  83  Linux
/dev/sdb7            6113       19457   107193681   83  Linux
```  

sdb1 is probably the recovery partition, sdb2 is the Windows partition I am trying to boot into.

Any ideas what to do?


Edit: Solved it by changing the Grub entry to:

> title Microsoft Windows
root (hd0,1)
savedefault
makeactive
chainloader +1

---

