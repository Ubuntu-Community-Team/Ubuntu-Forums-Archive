---
title: "Grub problem for dual boot"
date: 2012-02-19
forum: General Help
---

### Post by gramsyn on 2012-02-19
Hello,

I had a dual boot system Ubuntu/Windows at seperate physical drives. I had to remove the Win Drive though, so I installed Windows at a different partition at the Ubuntu Drive. Everything worked, until I removed the second drive.

Grub finds both Ubuntu and Windows, but boots only Ubuntu. When I select Windows, I get an error message.

I tried to fix it by WinCD from Strartup Repair, but cannot find the Windows Installation. It says that it cannot find any drive! It is a modern WD drive, so I suppose it is not rational.

Any ideas?

---

### Post by ajgreeny on 2012-02-19
Have you run ```
sudo update-grub
``` in terminal of your Ubuntu install?  That should find the new windows and add it to the grub menu for you.

---

### Post by @gu79 on 2012-02-19
Have you updated grub? (sudo update-grub)

---

### Post by oldfred on 2012-02-19
If sudo update-grub does not let you boot, post the boot info script from Boot Repair.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

