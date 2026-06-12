---
title: "deleting Grub line"
date: 2010-05-25
forum: General Help
---

### Post by jesse c on 2010-05-25
I upgraded to 2.6.33 and my comp will only run in Low graphics mode so i scroll down one level back to 2.6.32-22 and all is fine.How can i 'erase' the 2.6.33 line (and the associated recovery line)from the grub list so i dont have to deal with it till bugs are removed later on.My Grub header says it is version 1.98-1ubuntu6

---

### Post by dino99 on 2010-05-25
goto synaptic and select by right clicking on the kernel you want to remove (header and image packages)

then

sudo update-grub

---

### Post by masux594 on 2010-05-25
If you have install the 2.6.33 kernel and u don't wanna use it, you may uninstall it and then automatically erase the 2.6.33 lines in the boot kernel choose.. instead if u want to keep the kernel, delete te two groups in the bottom of the grub.conf where u can find the 2.6.33 kernel.. To edit this file, type this command, change, save and then reboot..
```
sudo gedit /boot/grub/grub.cfg
```
There's only one thing.. If you have the kernel 2.6.33 installed, the next time that grub will be reconfigured, the two lines re-appear.. so, in my opinion, is better to uninstall the unuseful kernel..

Sysc, A

---

### Post by jesse c on 2010-05-25
dino99 i went to synaptic and deleted header and image of "33"but when i 'sudo update grub' the 33 stuff is still at the top of the list and when i reboot, the grub list is still the same and it boots into 33 unless i scroll down to 32 before auto boot

---

