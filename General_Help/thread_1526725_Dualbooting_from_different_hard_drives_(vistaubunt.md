---
title: "Dualbooting from different hard drives (vista/ubuntu)"
date: 2010-07-08
forum: General Help
---

### Post by richard.dunne on 2010-07-08
Im not sure if this post is in the right place but heres my problem.

I have 2 hard drives and I want to know if i can use grub2 to boot from both of them from one menu. on a 160gb sata I have windows vista (installed first but HDD was removed while I installed Ubuntu) and on a 40gb ata/ide hard drive I installed ubuntu.

can anyone help me?

---

### Post by oldfred on 2010-07-08
welcome to the forums.

You have total control of grub. Grub2 is very good at finding other systems and adding them to the menu to let you boot either system.

Mixed PATA/SATA drives sometimes causes issues as the BIOS or grub may mount the PATA drive first. Does you BIOS let you choose boot drive. Or does PATA become boot drive.

In Ubuntu you can run this to find the windows install:
sudo update-grub

---

