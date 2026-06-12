---
title: "Beta Grub"
date: 2010-05-05
forum: General Help
---

### Post by ibbill on 2010-05-05
On the boot up screen of lucid the grub reads as  Beta 1.98-1 ubuntu6.

Is this correct. This is a fresh install of 10.4.

---

### Post by WorMzy on 2010-05-05
Yes, Ubuntu now uses the beta of Grub2 as the default bootloader, although Grub legacy is still available in the repos if you would rather use that.

---

### Post by ibbill on 2010-05-05
WorMzy thanks for the quick reply. Everything seems to be running fine so will leave it as is. Thanks again

Bill

---

### Post by WorMzy on 2010-05-05
No problem. Just be aware of the changes between the two versions. For example, menu.lst has been replaced with grub.cfg, which is automatically generated based on the contents of a bunch of config files stored at /etc/grub.d; to update grub's menu, you need to edit these files, then run 'sudo update-grub'.

---

### Post by ibbill on 2010-05-05
Thanks again  All that you have kindly posted are above my ability and knowledge of Ubuntu. So I will leave well enough alone.
I hope the ubuntu team just gave me the best of the 2 types of grub.

---

