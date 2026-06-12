---
title: "how to install program on Ubuntu Virtual machine"
date: 2011-06-15
forum: General Help
---

### Post by emanhossny on 2011-06-15
Hello,
I have Windows xp & i created virtual machine for ubuntu os to run on my host(windows Xp).
I need to install program to run on ubuntu VM, the source code of the program exists on the Disk(& i can see it from windows) but I can't see it on ubuntu VM, can anyone help me to install the program?

---

### Post by falko on 2011-06-15
You can use WinSCP to transfer files to your Ubuntu VM.

---

### Post by grahammechanical on 2011-06-15
Does the VM program allow Ubuntu to use the CD drive? Do you not need to change a setting in the VM program? In Ubuntu use the Disk Utility program to see if the CD drive is listed. Try it with a disk in the drive. You may be able to use Disk Utility to mount the CD drive (tell the OS that the CD drive is there and should be accessed).

Regards.

---

### Post by emanhossny on 2011-06-17
many thanks for all replays, i will try to check each one & tell u.

---

### Post by 3rdalbum on 2011-06-17
Virtual machine programs can usually create a Shared Folder that appears to Ubuntu like a network share.

---

### Post by mister_playboy on 2011-06-17
> **3rdalbum said:**
> Virtual machine programs can usually create a Shared Folder that appears to Ubuntu like a network share.

Press F1 in VirtualBox to bring up the manual and go to section 4.3 "Shared Folders" to learn how to do this.

---

