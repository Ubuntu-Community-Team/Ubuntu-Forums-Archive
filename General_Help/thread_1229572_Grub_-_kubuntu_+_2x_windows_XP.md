---
title: "Grub - kubuntu + 2x windows XP"
date: 2009-08-02
forum: General Help
---

### Post by nooby12 on 2009-08-02
Hi,
I use Kubuntu 9.04 x64 and Windows XP.
I have Windows XP (twice-i really need both) and kubuntu installed on same hd.
I want to choose between ubuntu and both Windows XP in grub.
I don't want to choose between Windows in Windows boot loader.
:confused:

Thanks for reply,
nooby12

---

### Post by linuxguy13 on 2009-08-04
I'm not sure about kubuntu but I know about ubuntu


I think you have to uninstall ubuntu. Once you uninstall install with a partition.

---

### Post by dandnsmith on 2009-08-04
I understand your problem (I have it too).

The thing to remember is that the Windows bootloader isn't set up to work the same way as grub and Ubuntu - for the 2nd install you won't have all the files needed for the boot from grub to be successful (I've tried copying them from one to the other, still without it working).

I think there may be some hidden info, which I haven't yet located - so the best I've achieved is to modify the setup so that the choice is all done from the Windows boot (you still use grub, but can make it effectively invisible for only one linux).

---

### Post by oldfred on 2009-08-04
I had windows on two different drives which used the map command in GRUB. I think the command in GRUB is the hide command  for partitions on the same drive, since windows likes to be first and only so GRUB has to hide the other windows install.
[http://www.bo.infn.it/alice/alice-doc/mll-doc/linux/advanced/node50.html](http://www.bo.infn.it/alice/alice-doc/mll-doc/linux/advanced/node50.html)

[http://www.justlinux.com/forum/archive/index.php/t-150551.html](http://www.justlinux.com/forum/archive/index.php/t-150551.html)

---

### Post by nooby12 on 2009-08-15
Thank you for answers.
I'll try all today and tell the results.

---

### Post by nooby12 on 2009-08-21
I tried that:

[http://www.justlinux.com/forum/archive/index.php/t-150551.html](http://www.justlinux.com/forum/archive/index.php/t-150551.html)

But I get an error Invalid device requested. when booting and seconnd windows don't boot.
I have a strange parititon table:

1: windows 1st install (80gb)
2: linux ext3 (mounted on /)(10gb)
3: Linux swap (8gb)
4: linux ext3 (mounted on /home) (80gb)
5: NTFS partition without OS, just for files (
320gb)
6: windows 2nd install (80gb)

Thanks for any help.

---

