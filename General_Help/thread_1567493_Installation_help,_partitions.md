---
title: "Installation help, partitions"
date: 2010-09-03
forum: General Help
---

### Post by Riffer on 2010-09-03
I've taken my 300 gig HD and have partitioned it into 3 equal sizes.  1 is my present 10.04 install and 3 is my /home folder.  I would like to install 10.10 onto 2.  

My questions is: how will this affect my present setup, can I use my present /home partition for both installs?

Thanks for your help.

---

### Post by cj.surrusco on 2010-09-03
It is normally not recommended to use the the same /home partition for more than one install, So you would probably want to make a fourth partition as /home for the new install. 

As far as the bootloader, you just need to run update-grub for grub to detect the old Ubuntu install so you can boot into that as well. 

Those are the only obvious problems that you might encounter.

---

### Post by Riffer on 2010-09-03
Thanks, kinda what I thought.  Now to figure out how big I want partitions.

---

