---
title: "I Zero'd my MBR, recovery still possible?"
date: 2012-02-27
forum: General Help
---

### Post by ag93ds on 2012-02-27
I ran this command

```
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
```

...on the wrong device. Now I can't get into the drive at all. Is recovery at all possible?

---

### Post by wildmanne39 on 2012-02-27
Hi, did you let it run until completion, how many writes did it make? It is very hard to recover data after using that command it does stand for data destroyer.
Thanks

---

### Post by Herman on 2012-02-27
The partition table is probably the most important part of your hard disk's MBR.
You should be able to use an app called 'TestDisk' which is installable in Ubuntu or in the Ubuntu Live CD.  TestDisk can be used to scan your hard disk for partitions and write a new partition table. The TestDisk website contains how-tos to show you out how to use it, you just need to take a look around to find them.

Another important part of a hard disk's MBR is the area for the boot loader code.
You just need to re-install GRUB to fix that part.

If you're running Ubuntu by itself you'll be fine after that and your computer should work as normal again, you can go back to having fun or working.

If you have a recent version of Windows  you will need to recover your data and re-install I think, since the Windows boot loader is fatally bound to the MBR's 'Disk Signature', I imagine as part of their anti-piracy strategies. I don't know of any way you can get this 'Disk Signature' back once it's erased unless you have a backup copy of the MBR (usually made with the dd command).

---

