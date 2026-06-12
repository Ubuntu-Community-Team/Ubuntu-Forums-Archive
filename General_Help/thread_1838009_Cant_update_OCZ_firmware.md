---
title: "Cant update OCZ firmware"
date: 2011-09-02
forum: General Help
---

### Post by qwsed on 2011-09-02
According to OCZ webpage i should use:

 Type fwupd <device>
Ex. 
For one drive, sdb
fwupd /dev/sd

But when i do (iam in the folder the file is in) i get the message:

"fwupd must be run as root" i dont understand at all... please help me

---

### Post by qwsed on 2011-09-02
The firmware is located at the desktop... If any kind sould could please type the command to execute it. I know nothing about ubuntu

---

### Post by qwsed on 2011-09-02
Desktop -> linux32 -> fwupd file. Pretty please? :)

---

### Post by SirDrexl on 2011-09-03
Type "sudo" before the command, so it should be

"sudo fwupd /dev/sdb"  

Note that the last letter refers to the drive you want to update.  It might be a instead of b.

Basic Ubuntu info: normally you are a limited user, not the root.  Prefacing a command with sudo will temporarily allow you to perform a task that requires root privileges.

---

