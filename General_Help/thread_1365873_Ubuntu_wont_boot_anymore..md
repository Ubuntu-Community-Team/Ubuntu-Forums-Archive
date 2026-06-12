---
title: "Ubuntu wont boot anymore."
date: 2009-12-27
forum: General Help
---

### Post by catsonmars02 on 2009-12-27
I installed Ubuntu a couple week's ago on a separate partition from my windows vista partition and it worked fine until last night.  When I select Ubuntu during the boot process and I select how it should boot the screen stays blank until I press my power button then I get
/host/ubuntu/disk/root.disk does not exist. Dropping shell.

In my image file I have:
 boot.catalog
boot.img
root.img

So what's the deal here?
Since my installation I also installed Winserver 2008 on a seperate partition.

---

### Post by QrK0 on 2009-12-28
Probably win2008 has rewritten the boot sector on the disk. You can try to repair grub with the ubuntu cd.

---

### Post by catsonmars02 on 2009-12-28
See that's what I was thinking but I thought it was odd because all my OS's are on seperate partitions.  So where they boot from is all in one place if I understand correctly?  The winserver 2008 took more space than I expected, I had 140MB free now I have like 20MB could this be the problem?

---

### Post by QrK0 on 2009-12-28
The boot sector is not located in a partition. The boot sector is located at the hard disk. Take a look at the Wikipedia: [http://en.wikipedia.org/wiki/Boot_sector]("http://en.wikipedia.org/wiki/Boot_sector")
Hope it helps you

---

