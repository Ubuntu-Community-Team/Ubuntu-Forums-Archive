---
title: "If i don't use Ubuntu for a week, it doesn't work anymore"
date: 2010-06-22
forum: General Help
---

### Post by ayozito on 2010-06-22
Hi! I have a little rare problem..
 
If i use my Ubuntu some times per week, there isn't any problem. But if i don't use it for a short time (a week), when i want use it again and select it on GRUB.. after the first loading screen (on Ubuntu 10.04 the purple screen with Ubuntu in white and some points under), my screen is black.
 
The computer screen is receiving signal because the led is green and not brown/orange like when is on standby mode.
 
On Windows i haven't any problem.
 
First time it happened with Ubuntu 9.10. I didn't got solution for it and  i format the partition and install the 10.04. But now it happen again with 10.04.
 
I have an ATI 5770 and i have tried drivers since 9.12 till 10.4 (last ones the best i have had)
 
On versions before 9.10 i had no problem, but i can't confirm that, because i had other graphic card (NVIDIA 9800GT). But the 5770 didn't work well on previous version so i updated to 9.10 and after this problem, updated to 10.04.
 
 
At spanish forum, people don't know solution for this problem, they never read about a similar problem. I hope you know a solution for it, because the only one i found and work is.. format and reinstall.

---

### Post by justleen on 2010-06-22
When at the black screen, can you still switch to a terminal? (ctrl-alt-F2)

If so, what happens if you restart X from there?
```

sudo service gdm restart 
```

---

### Post by Mark Phelps on 2010-06-22
I read about a similar problem where someone could use Ubuntu again and again without problem, but if they booted into MS Windows, when they tried to go back to Ubuntu, they had the same problems as you.

In their case, their machine had two video devices -- an onboard chip and an add-on card, and they had the onboard chip selected in the BIOS for MS Windows.  So, when they returned to Ubuntu, the machine was set to see only the onboard video chip, rendering the Linux drivers for the videocard useless.  They had to go into the BIOS and change a video selection setting.

---

### Post by ayozito on 2010-06-22
ok, just solved it. Was drivers issue. I logged using the rescue mode of grub and unisntalled drivers and reinstalled others and is working

---

