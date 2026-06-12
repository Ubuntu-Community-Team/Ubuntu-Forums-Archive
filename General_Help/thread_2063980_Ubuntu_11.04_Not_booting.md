---
title: "Ubuntu 11.04 Not booting"
date: 2012-09-28
forum: General Help
---

### Post by thewhiteeye on 2012-09-28
I installed Ubuntu 11.04 alongside windows XP. I booted into ubuntu two times and both times it worked fine. Now when I boot into ubuntu, it shows the following:


[B]BusyBox v1.17.7 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [/B]

and the cursor blinks at the end.

Please help me with this

Thanks

---

### Post by daslinkard on 2012-09-30
What size partition did you allow for when creating one for Linux?

---

### Post by daslinkard on 2012-09-30
It also seems that a way around it may be as follows:

> Fixed it by opening grub menu (holding shift during startup) then  choosing the recovery mode (there were 2 recovery modes, I chose the  lower one ending in .31). It gave me the option then of fixing broken  packages, which it then did automatically. It then allowed me to  continue normal boot. This opened another command line screen, but with  my login and password required, much like the terminal. After typing in  login and password I  typed "sudo reboot", entered my sudo password and  everything was back to normal. 

---

