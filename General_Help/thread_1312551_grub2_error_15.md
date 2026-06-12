---
title: "grub2 error 15"
date: 2009-11-03
forum: General Help
---

### Post by H4F on 2009-11-03
I installed grub2 . after restart I get Error 15.
I  found few guides how to fix that but can't follow them cause 
grub /bin/sh not found.
I have:
/dev/sda1 /
/dev/sda3 ntfs
/dev/sda5 /boot
/dev/sda6 /home
/dev/sda7 /swap

I use / as root file system to execute shell in the installer environment.
/bin/sh: grub: not found

---

### Post by drs305 on 2009-11-03
You might try reinstalling grub 2 from the LiveCD. Remember to run the extra command since you have a /boot partition. Here is link from the Ubuntu community doc:
[Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by H4F on 2009-11-03
now I installed grub 2. but seems that it does not know where to boot from. 
I am in grub boot shell
what should I do ?

---

### Post by drs305 on 2009-11-03
> **H4F said:**
> now I installed grub 2. but seems that it does not know where to boot from. 
I am in grub boot shell
what should I do ?

From the same link, there is a section on booting from the command line. There are instructions on how to boot from the 1) menu via editiing, 2) from the "grub" prompt, and 3) from the "grub-rescue" prompt.  Look at the "CLI" part of the linked page.

---

### Post by Axel-P on 2009-11-03
I don't know if the problem is solved. But [this here]("http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04") helped me a lot while installing grub2

GL
Axel

---

### Post by H4F on 2009-11-03
> **Axel-P said:**
> I don't know if the problem is solved. But [this here]("http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04") helped me a lot while installing grub2

GL
Axel

thanks. I just reinstalled old grub. will stick with it by now.

---

