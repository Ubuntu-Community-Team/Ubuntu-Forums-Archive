---
title: "Ubuntu 9.10/10.04 grub2 mount by uuid problem"
date: 2010-04-24
forum: General Help
---

### Post by NaitoNeko on 2010-04-24
Using a M2N32-SLIDeluxe MOBO, both OS crash trying to start. It says that the timeout trying to boot from my sata device was reached.
It seems that is a problem trying to boot/mount the HD by uuid, because all the other systems that does not use grub2 has problems.

Anyone knows how to fix this ?
or
Anyone had this problem ?
or
Can anyone help me ? :lolflag:

---

### Post by oldfred on 2010-04-24
Possibly this error. Also see his main page as he has fixes for other issues also:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

---

### Post by NaitoNeko on 2010-04-24
I will try that solution, and i will let you know. I'll try it with the 10.04rc.

---

### Post by NaitoNeko on 2010-06-14
I realized that the problem is because I have 2 HD that are equals and Ubuntu try to use it like a Ride drive.

I tried to disable dmraid, but it did not detect any drives.

The only thing that works was disconect one of the drives. If anyone have an othe solution, plz let me know :P.
:guitar:

---

