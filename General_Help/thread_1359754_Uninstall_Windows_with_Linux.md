---
title: "Uninstall Windows with Linux"
date: 2009-12-20
forum: General Help
---

### Post by Gizhy on 2009-12-20
I've downloaded Linux Ubuntu onto my Windows 7 and I want to know if I can take off Windows and how to if possible without harming the Linux OS installed onto my computer.

Any help would be greatly appreciated.

---

### Post by James78 on 2009-12-20
If you installed Linux onto Windows, then you cannot take off Windows without loosing Linux. You could try backing up the hard drive file, it's somewhere in c:\my program files\<program folder>

I suggest installing Linux separately on a new partition as ext4, that way it is truly "independent" and doesn't rely on the Windows being installed.

Also, please note that if you delete Windows anyways, your MBR will be messed up, and will need to be fixed. This can be done easily by installing Windows or Linux again, however just make sure you have an installation disk readily available. (There will likely be an invalid MBR in Grub linking to that specific Windows 7 MBR, just delete that entry)

---

### Post by Gizhy on 2009-12-20
Alright, thanks a lot. I appreciate it.

---

### Post by radamez85 on 2009-12-20
Sorry but how do you know if ubuntu is installed independently or not ?
I want to remove windows as well. =D

---

### Post by James78 on 2009-12-20
Now, if you backup the hard disk file from Windows, you may be able to mount the file in Linux, although I am not exactly sure what type of file it currently is.

If you'd like to run a dual boot, this is easy. Just first install Windows again, then install Linux after and Windows should automatically be added to Grub.

Good luck.

> **radamez85 said:**
> Sorry but how do you know if ubuntu is installed independently or not ?
I want to remove windows as well. =D
You can know this by how you installed it. Did you insert the Linux disk into Windows and install it on Windows (using Wubi)? Or did you restart your computer and install from there? Installing from Windows means Linux will be installed under the Windows filesystem as a program, and installing from a reboot means it goes into it's own partition, usually as ext4.

You can also remove Windows by removing the partition when you're installing Linux from a proper reboot (not installing inside any other OS).

---

