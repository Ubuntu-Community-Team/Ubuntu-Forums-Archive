---
title: "What to list in menu.lst (grub)"
date: 2010-10-09
forum: General Help
---

### Post by gannggstaz on 2010-10-09
I have debian installed in my primary partition as /dev/sda1, my /home parition as /dev/sda2, swap as /dev/sda3, and another OS in /dev/sda4. In my grub.conf hd(0,0) is the appropriate root for debian, how do I determine the correct one for my other OS? I know all other details.

---

### Post by andrewthomas on 2010-10-09
> **gannggstaz said:**
> I have debian installed in my primary partition as /dev/sda1, my /home parition as /dev/sda2, swap as /dev/sda3, and another OS in /dev/sda4. In my grub.conf hd(0,0) is the appropriate root for debian, how do I determine the correct one for my other OS? I know all other details.
If you are using legacy grub ( 0.97 ) the root of your 'other OS' on sda4 would be hd(0,3). Grub2 which starts the partition numbering at 1, grub starts the numbering at zero.

---

