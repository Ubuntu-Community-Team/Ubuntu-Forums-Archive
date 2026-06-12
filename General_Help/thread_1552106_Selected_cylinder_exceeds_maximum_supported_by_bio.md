---
title: "Selected cylinder exceeds maximum supported by bios"
date: 2010-08-13
forum: General Help
---

### Post by molykkutti on 2010-08-13
" Selected cylinder exceeds maximum supported by bios  "  

I got this errot message when i tried to select Ubuntu ( 9.04 ) from a dual booting menu ..
I dont know how to solve this problem .. please help ...

---

### Post by Fafler on 2010-08-13
Is it a new installation? If so, reinstall and when asked to partition, do it manually and make a 100 mb /boot partition just after your windows partition. Fill the rest with / and swap. If the problem persists, make the windows partition smaller, until the windows partition + entire /boot partition fits under what the BIOS is able to access.

---

### Post by lokojones on 2010-08-13
Your grub config seems to be broken. Did it work ever, or did you get this right after install? If so, what did you do before it broke?

---

### Post by oldfred on 2010-08-13
More info here on old grub error, & suggestions on how to fix:

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

### Post by molykkutti on 2010-08-18
thanks to all for the helping hands  :)

---

