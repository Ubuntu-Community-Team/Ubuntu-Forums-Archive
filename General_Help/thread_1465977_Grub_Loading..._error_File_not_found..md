---
title: "Grub Loading... error: File not found."
date: 2010-04-29
forum: General Help
---

### Post by alqin on 2010-04-29
Hello Ubuntu,

Have an Asus EEE PC 901 and an some old 40GB HDD witch is pluged in in one of the right usb ports with a help of a rack. 
What i want is to install Ubuntu 10.04 on one of the partitions from 40GB external HDD.

I did the following steps:
1. From bios where is something like Disk Boot priorities i chosen the external HDD.
2. At boot time I pressed ESC to chose USB drive witch has Ubuntu 10.04 netbook edition.
3. When asked where do i want to install Ubuntu, I selected the last option with the partitions.
4. I selected from the external HDD a partition that has 10 GB. On advanced options I selected that partition to be formated with Juliet 4ex file system(or something... anyway something with 4ex). On boot location(or something...) I chosen \. This HDD also has a swap partition with something like 512MG from some years ago when I also played with Ubuntu on this HDD.
5. At the end, on the last screen before installing Ubuntu, I clicked advanced and i clicked to not install boot loader(or something...)
6. I installed Ubuntu.

Now If i chose from bios at disk priorities or at boot time with ESC the external HDD it should be loading Ubuntu otherwise should be loading whatever operating system is on netbook only that insed of Ubuntu loading i get this error:

Grub Loading...
error: File not found...
Grub rescue

I also have to mention that I installed Ubuntu 10.04 beta 2 and it worked just fine. From the last beta it did not worked anymore

Alqin

---

### Post by oldfred on 2010-04-30
Welcome to the forums.

If you chose with the advance button not to install a boot loader it will not boot. You should install grub to the external drive and leave your current boot loader on the internal.

Instructions here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by alqin on 2010-04-30
Thank you **oldfred**. Problem solved.

---

