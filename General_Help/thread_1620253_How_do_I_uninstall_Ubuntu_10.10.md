---
title: "How do I uninstall Ubuntu 10.10?"
date: 2010-11-12
forum: General Help
---

### Post by mikewgard on 2010-11-12
I have Ubuntu 10.10 dual booting with Windows 7. No problems, although I have installed Ubuntu on another computer and wish to UN-install Ubuntu from the dual boot machine. How can I uninstall Ubuntu and recover the portion of the hard drive dedicated to Ubuntu?

---

### Post by 73ckn797 on 2010-11-12
If installed on separate partition you can boot from a live CD and delete the partition for Ubuntu. Then boot from the Windows CD and enter recovery mode. I do not use Win7 so you will have to look around for how to rewrite the MBR for Windows. It used to be ```
fixboot
``` from the command line. Win XP used ```
fixmbr
```.

---

### Post by ivarn on 2010-11-12
Or u can use disk manager in  windows to delete the partition and use the windows cd to repair the boot loader.

---

### Post by garvinrick4 on 2010-11-12
Has xp,vista and 7.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by 73ckn797 on 2010-11-12
> **ivarn said:**
> Or u can use disk manager in  windows to delete the partition and use the windows cd to repair the boot loader.
What about recovering the disk space? I have used the Ubuntu CD to do that. I do not know of any way to resize from Windows. Windows will still need the MBR restored as we both suggest. I do know that after resizing with the Ubuntu CD Windows will need ```
chkdsk
``` in order to restart Windows again.

Gavinrick4 has the best info in the link.

---

