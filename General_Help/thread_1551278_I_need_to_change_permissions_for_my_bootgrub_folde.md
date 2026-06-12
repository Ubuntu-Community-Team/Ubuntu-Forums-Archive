---
title: "I need to change permissions for my /boot/grub folder."
date: 2010-08-12
forum: General Help
---

### Post by P-Geist on 2010-08-12
Hey Community,

This is my 2nd time using my Ubuntu, I am using 9.10 because my laptop doesnt support 10.04 (need more RAM :D) So anyway i need to know a way to change it so i can edit files in there, i checked the properties and root has read only permissions how can i change this?

Thanks,
Todd

---

### Post by geoffjay on 2010-08-12
You don't want to change those permissions. Instead you should use sudo/gksudo, eg. gksudo gedit /boot/grub/grub.cfg

But before you do that, you're not actually supposed to edit those files directly anymore ever since the change to grub2. Instead you should make your changes to /etc/default/grub & /etc/grub.d/*, after making changes there you update your /boot/grub files using the command

sudo update-grub

---

### Post by P-Geist on 2010-08-12
i basically just need to delete the "no floppy" part of the boot commands....

---

### Post by geoffjay on 2010-08-12
Every time that the kernel gets an upgrade a call is made to update-grub and what you have there now will show up again regardless of whether or not you delete it. Hence the need to edit the files mentioned previously. Or you can just remember to delete the no floppy part every time there's a kernel upgrade.

There's a suggestion here ([http://ubuntuforums.org/showthread.php?t=1194714&page=2](http://ubuntuforums.org/showthread.php?t=1194714&page=2)) for removing --no-floppy from the update-grub tool.

Have a look at [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for info on grub2.

---

