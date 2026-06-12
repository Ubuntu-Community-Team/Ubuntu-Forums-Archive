---
title: "Grub Rescue; can't boot"
date: 2011-02-03
forum: General Help
---

### Post by Kivi1831 on 2011-02-03
Hi,


I'm having a big problem with Ubuntu 10.10.
I had a W7Starter double boot and while checking disk management in Windows 7, I accidently deleted my Linux partitions (yeah stupid me...)


I get the following message when I try to boot now:
erroe: unknown filesystem.
*[I]grub rescue>*
[/I]


Needless to say I'm panicking a bit. The thing is that I can't even boot with a LiveUSB as I get this message immediately after I turn my netbook on. I can't reach BIOS or anything.


Could anybody help?
Thanks.

Pierre

---

### Post by datealz on 2011-02-03
since your partition is gone you need to fresh install ubuntu again all of your previous data is lost from ubuntu's partition

---

### Post by bcbc on 2011-02-04
You shouldn't have a problem booting from USB or CD - some computers have a 'fastboot' option enabled so you have to find out how to switch that off and get the BIOS boot menu.
If you boot an Ubuntu CD/USB and install testdisk you can probably just recover those partitions, provided you haven't created new ones and modified the portion of the disk they are on. Even 'formatting' a partition can be recovered using testdisk. 

So try that first.

---

