---
title: "Old kernels do  not appear on boot screen"
date: 2012-02-08
forum: General Help
---

### Post by cscj01 on 2012-02-08
At some point, old kernels stopped appearing on my boot screen.  I am not aware I did anything to change this.  I run 11.10_x64.  Is there a setting or something I should check?

---

### Post by KingYaba on 2012-02-08
You can check the grub.cfg file found in /boot/grub/grub.cfg. I regularly edit mine to take out old kernels I don't use. You can run the update-grub command in the terminal and that may do the trick of putting back all your old kernel versions.

---

### Post by pixiq on 2012-02-08
Select 'Previous Linux versions' in the grub menu :-)

---

### Post by cscj01 on 2012-02-08
Okay, I guess I misssed the "Previous Linux Versions" line.  Thanks.

---

