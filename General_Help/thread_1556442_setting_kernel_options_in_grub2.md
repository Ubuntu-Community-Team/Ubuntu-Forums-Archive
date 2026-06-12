---
title: "setting kernel options in grub2"
date: 2010-08-19
forum: General Help
---

### Post by laverde on 2010-08-19
Hi,

I have a problem with my touchpad, sometime it doesn't work at start-up and this happens randomly. I have looked around and  maybe I could solve this with the procedure described in 

      [http://ubuntuforums.org/showthread.php?t=1061867](http://ubuntuforums.org/showthread.php?t=1061867)


I'd like to add the equivalent of 

      i8042.reset i8042.nomux i8042.nopnp i8042.noloop 

to kopt in the old grub.

I looked into the grub2 documentation, 

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

but I am very confused.
I am not even sure if I have to modify /etc/grub.d/40_custom or 10_linux.

Do anybody know what to change?

thanks in advance

---

### Post by Elfy on 2010-08-19
add options to the GRUB_CMDLINE_LINUX_DEFAULT= line of /etc/default/grub then run sudo update-grub

---

### Post by Cavsfan on 2010-08-19
Then once you get it all fixed up, you'll want to take a look at the tutorial in my signature.
It simplifies things.

---

### Post by Vaphell on 2010-08-19
[http://ubuntuforums.org/archive/index.php/t-953995.html](http://ubuntuforums.org/archive/index.php/t-953995.html)

> grover66
October 28th, 2009, 03:36 AM
modify /etc/default/grub;

edit the line;

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"

(all one line)

then run;

update-grub


---

### Post by laverde on 2010-08-19
@forestpiskie and @Vaphell

thanks for the answer and the immediacy, I hope this will solve my touchpad issue.

@Cavsfan

thanks, I will give a look

bye

---

