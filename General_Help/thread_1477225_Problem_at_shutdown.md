---
title: "Problem at shutdown"
date: 2010-05-08
forum: General Help
---

### Post by fmonso on 2010-05-08
I've just installed 10.04 over 9.10. Runs smoothly until I try to logout and shutdown. There is only one user, it logs out, but instead of shutting down the system, prompts me again to log in. It happens also if I choose reboot instead of shutdown.

Another (minor) problem. The boot menu (grub) offers me the two versions of Ubuntu: 9.10 and 10.04. Does it mean I have two Ubuntus in my PC? I thought I have made an actualization.

---

### Post by wwwil on 2010-05-08
For the first issue try shutting down using the terminal and see if you get the same problem ("sudo poweroff" and enter your password to shutdown). 

For the second problem try updating Grub ("sudo update-grub") and see what operating systems it finds.

---

