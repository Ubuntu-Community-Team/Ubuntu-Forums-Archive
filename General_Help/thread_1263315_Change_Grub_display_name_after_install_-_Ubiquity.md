---
title: "Change Grub display name after install - Ubiquity"
date: 2009-09-10
forum: General Help
---

### Post by morpheus063 on 2009-09-10
Hi All,

I am trying to make a Custom Ubuntu Live CD using [COLOR=DarkRed]**Remastersys**[/COLOR] and an installer for the Live CD using **[COLOR=DarkRed]Ubiquity[/COLOR]**.  I was able to successfully create a Custom live CD using remastersys and when I boot from the custom Live CD – the grub correctly displays the Custom Live CD Name that I specified during the ISO file creation using remastersys. However, when I install from the Live CD that I created, using Ubiquity, after reboot, the Grub menu displays as Ubuntu and not the Custom Label. 

How can I change it so that after installation, the custom Live CD name is displayed?

Thanks in advance.

-M-

---

### Post by Zifnab06 on 2009-09-10
When Grub installs, it defaults to the Ubuntu-(kernelversion) whatever it is. 

If you go and edit your /boot/grub/menu.lst (i think) you should be able to rename the ubuntu boot option in grub after it is installed on the computer.

---

### Post by morpheus063 on 2009-09-10
> **Zifnab06 said:**
> When Grub installs, it defaults to the Ubuntu-(kernelversion) whatever it is. 

If you go and edit your /boot/grub/menu.lst (i think) you should be able to rename the ubuntu boot option in grub after it is installed on the computer.

Thanks Zifnab06 for the quick response. However, is there any way we can change the defaults of "Ubuntu-(kernelversion)" through any means or "hacks". There has to be some way - thats what I feel.

Thanks once again.

---

### Post by akakingess on 2009-09-11
Could you run a script right after install to do the renaming within GRUB as zifnab06 was suggesting?

---

### Post by Zifnab06 on 2009-09-11
Hi again, 

If it can be done, I don't know how to do it. You should be able just to set up a .sh script you can run when you start ubuntu for the first time to change the correct line. I was tyring to find the actual installer for ubuntu on my livecd, and its all in an isolinux format which I know almost nothing about. 

Sorry I couldn't be of more use!

---

