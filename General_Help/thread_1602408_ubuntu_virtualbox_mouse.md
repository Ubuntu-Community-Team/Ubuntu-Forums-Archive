---
title: "ubuntu virtualbox mouse"
date: 2010-10-21
forum: General Help
---

### Post by RastaManPower on 2010-10-21
hello guys i have seen on the net that there is a tool that will let me move mouse cursor from guest to host without pressing the ctrl key.. hos is this tool called? i cant find it

---

### Post by Quackers on 2010-10-21
VirtualBox Guest Additions.

---

### Post by uRock on 2010-10-21
> **Quackers said:**
> VirtualBox Guest Additions.
+1 [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

---

### Post by LowSky on 2010-10-21
EDIT: Beat me to it

---

### Post by RastaManPower on 2010-10-21
ok i followed the guide... the mouse thing now works but i dont understand this:
#

Change to the directory where your CD-ROM drive is mounted and execute as root:

sh ./VBoxLinuxAdditions-x86.run

In a 64-bit Linux guest, use VBoxLinuxAdditions-amd64.run instead.



how do i use usb sticks on windows xp now?

---

### Post by pqwoerituytrueiwoq on 2010-10-21
[http://forums.virtualbox.org/viewtopic.php?f=9&t=27820](http://forums.virtualbox.org/viewtopic.php?f=9&t=27820)
you could set the usb as a network shared folder

---

### Post by uRock on 2010-10-21
> **RastaManPower said:**
> ok i followed the guide... the mouse thing now works but i dont understand this:
#

Change to the directory where your CD-ROM drive is mounted and execute as root:

sh ./VBoxLinuxAdditions-x86.run

In a 64-bit Linux guest, use VBoxLinuxAdditions-amd64.run instead.



how do i use usb sticks on windows xp now?
If you host is WIndows or Ubuntu 10.04 or newer, then you should be able to just double-click the autorun file in the guest additions image.

---

### Post by RastaManPower on 2010-10-21
where is that i dont understand. my host is ubuntu 10.10 and my guest is windows xp

---

### Post by pqwoerituytrueiwoq on 2010-10-21
> **RastaManPower said:**
> where is that i dont understand. my host is ubuntu 10.10 and my guest is windows xp
for windows that would probably be the D drive

---

