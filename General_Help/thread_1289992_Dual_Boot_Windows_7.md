---
title: "Dual Boot Windows 7"
date: 2009-10-13
forum: General Help
---

### Post by vivaldibabe on 2009-10-13
I'm running ubuntu 9.04 Jaunty on my Acer laptop, and I'm curious if anyone thinks a newcomer could set-up/be helped to set-up a dual boot with Windows 7 and Jaunty.

I've been having some driver issues with Jaunty, and I'd also like to try 7....:cool:

---

### Post by kellemes on 2009-10-13
How I did it..
- Boot with the Windows 7 installdisk.
- Use the windows-partitioner to destroy every partition on the disk you want to use.
- Now have it create a new partition for Windows, but leave enough space for a Linux-install later on..
- Install Windows 7
- Install Linux in the free space you left after the Windows-partition, most distributions will 'detect' Windows and add an entry in your Grub bootmenu.

By the way.. Windows 7 is amazingly fast and works great on a modern machine like mine.

---

### Post by lovinglinux on 2009-10-13
> **vivaldibabe said:**
> I'm running ubuntu 9.04 Jaunty on my Acer laptop, and I'm curious if anyone thinks a newcomer could set-up/be helped to set-up a dual boot with Windows 7 and Jaunty.

I've been having some driver issues with Jaunty, and I'd also like to try 7....:cool:

See [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

If you want to preserve your current Jaunty installation, then you will have to restore the grub after installing Windows, otherwise you will boot only into Windows.

See [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by vivaldibabe on 2009-10-13
Awesome. =D
I'll let you know how it goes. Wish me luck!

---

