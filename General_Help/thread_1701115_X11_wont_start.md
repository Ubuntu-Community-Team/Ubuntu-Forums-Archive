---
title: "X11 wont start"
date: 2011-03-06
forum: General Help
---

### Post by moyam01 on 2011-03-06
I was installing dkms on my host Ubuntu 10.10 machine trying to get a Virtualbox forlder share going with an Ubuntu 9.10 virtualization. However, when I rebooted my computer it got stuck at the Ubuntu splash screen. 

I rebooted several times with the same outcome. I then went into Grub 2 and removed the quiet splash option and rebooted. Logged in and pressed Ctrl+F7 to see if it had an error but all I saw that it was stuck after it passed the battery check.

Went back to tty1 and gave the command sudo startx. It gave me the following two errors

(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers avaliable.

Fatal server error: no screens found

What do I do know?

Thanks in advanced.

EDIT: Also, I am using the nvidia proprietary drivers

---

