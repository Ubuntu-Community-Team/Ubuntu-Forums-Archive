---
title: "uswsusp problem"
date: 2010-08-25
forum: General Help
---

### Post by kurci2 on 2010-08-25
HI!
i have a serious problem
i have installed USWSUSP and enabled encrypt option for s2disk
i have also created RSA key.
hibernation went well, but when i want to resume it just don't ask me for a password
but when i tried recovery mode i ask me for a password, but when i type it and press enter nothing happens.

can i delete this resume image and perform a normal boot??

---

### Post by kurci2 on 2010-08-25
solution:
boot GPARTED.
format existing swap partition and reboot
everything works fine
set new partitiopn UUID in /etc/fstab
you're done

hope i will help somebody ones =)

---

### Post by TexasDex on 2011-03-12
I'm having the same problem.

This is marked as 'solved' because you were able to boot, but I don't think it really is, since the encrypted hibernate feature is still broken.

The [https://help.ubuntu.com/community/PowerManagement/Hiberate](https://help.ubuntu.com/community/PowerManagement/Hiberate) page says to use Alt+1 to show the prompt, and that works (hitting Esc also does it) but I still can't enter a password--nothing happens when I type or hit enter.  Not sure what's wrong with this...

---

### Post by Martin Pulec on 2011-03-16
Hi TexasDex, I have the same problem. I have just opened a bug ([https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/736487](https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/736487)) so if you have any additional information, you can add it there.

---

