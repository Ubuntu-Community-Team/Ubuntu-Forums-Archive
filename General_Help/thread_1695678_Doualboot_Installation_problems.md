---
title: "Doualboot Installation problems"
date: 2011-02-26
forum: General Help
---

### Post by Zwing on 2011-02-26
Hello
i have been tying too get a win 7 and Ubuntu 10.10 Dual boot too work.
i first installed win7 on he mian disk and have after that tried too install Ubuntu 10.10 on a nother (physikal) diffret drive.
i have tried the "install beside another operationg system" and i have tried too 2-3 diffrent tutorials where you use the manual (advanced) option too get a functional partition.. but everytime efter the installation is done and the system reboots i dont get the menu too choose operating system it just jumps too windows without any pardon..
is there any other option or is it something that i missed doing?

---

### Post by YesWeCan on 2011-02-26
It may be because your bios is set to boot the Windows disk first.
To get Ubuntu and the grub menu (which should allow you to choose either OS) the bios must be told to boot the Ubuntu disk first.

---

### Post by blueridgedog on 2011-02-26
You should either tell your PC bios to boot off of the second physical drive, or instruct the Ubuntu install to install grub to the master bood record of the first drive.  The first option should work with your current install.

---

### Post by YesWeCan on 2011-02-26
> **blueridgedog said:**
> You should either tell your PC bios to boot off of the second physical drive, or instruct the Ubuntu install to install grub to the master bood record of the first drive.  The first option should work with your current install.
That would be convenient in a way but I advise against it because, on occasion, a Windows update will replace the MBR and then the Ubuntu OS becomes unreachable. I consider it better all round to keep the Windows install on its own disk and never ever modified by Ubuntu or grub. :)

---

