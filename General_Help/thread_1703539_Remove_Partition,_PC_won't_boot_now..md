---
title: "Remove Partition, PC won't boot now."
date: 2011-03-09
forum: General Help
---

### Post by brerob708 on 2011-03-09
I have one hard drive that is partitioned: Windows7 and Ubuntu 9.04

I was in windows and I removed the Ubuntu Partition from my hard drive. When I restarted my computer, it now gives me the grub rescue> prompt (unknown filesystem).  I tried to run the Ubuntu Live CD to fix my problems from the command line, but it will not boot from CD giving me: "Buffer I/O error on device fd0,logical block 0)

I would like to have just a single partition that has Windows 7 and is actually able to boot.

Thanks!

---

### Post by vivek.pandey on 2011-03-09
i hope now you understand never to delete ubuntu partition when it is installed inside windows thinking that will uninstall ubuntu..sorry if i am being sarcastic...
do you have a windows reinstallation cd . i too once had done the same and then used windows cd to restore everything

---

### Post by oldfred on 2011-03-09
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Restore basic windows boot loader - universe enabled in Ubuntu
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Or use windows repair CD.
BootRec.exe /fixMBR

---

### Post by Mark Phelps on 2011-03-09
> **neo_aryan said:**
> i hope now you understand never to delete ubuntu partition when it is installed inside windows thinking that will uninstall ubuntu..sorry if i am being sarcastic...

Where did the OP say that Ubuntu was installed inside Windows?

They said they removed the partition -- and when you install inside Windows, no partition is created.

---

