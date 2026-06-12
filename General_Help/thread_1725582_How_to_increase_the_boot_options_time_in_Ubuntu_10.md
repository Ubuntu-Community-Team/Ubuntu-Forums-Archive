---
title: "How to increase the boot options time in Ubuntu 10.10?"
date: 2011-04-09
forum: General Help
---

### Post by kannanjagadeesan on 2011-04-09
Hi Experts,

I want to increase the boot options time in Ubuntu 10.10? I have got Ubuntu and XP - a dual OS in my computer. Sometimes, I want to select XP and the default choice time is very low that it runs into Ubuntu. How to change this - say about 30 seconds? 

With Kind Regards,
Kannan Jagadeesan

---

### Post by ~Plue on 2011-04-09
change the value of *GRUB_TIMEOUT=XX *in the file /etc/default/grub (run *gksu gedit /etc/default/grub*)
then after making the change. run [I]sudo update-grub
[/I]
//or try using the startupmanager from the repos. once installed, it'll be in the system > administration menu

---

