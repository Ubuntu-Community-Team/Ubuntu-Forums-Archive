---
title: "Removing grub screen."
date: 2011-06-02
forum: General Help
---

### Post by cracker89 on 2011-06-02
My friend just updated to 11.04, and since that he has the grub screen showing before loading into the actual OS. It wasnt there before. Its harmless I kno, and I told him so. 


But he would still like it to go away. I personally think that its because he has the previous version installed separately somehow, and uninstalling that would cause it to go away.

A little help? I think I might be getting a wee bit confused.. :)

---

### Post by chick_turk on 2011-06-02
No, it's there because of the Ubuntu install. It happened to me too. I would also like to figure out how to change the MBR order.

---

### Post by JCM_Pico on 2011-06-02
You can always do this:

gksu gedit /etc/default/grub

and the change the value of GRUB_TIMEOUT=5 (5 in my pc), to 0...

This way the grup menu wont appear, but it does not solve the reason for it to appear...

---

### Post by cracker89 on 2011-06-02
thats a good work around. will serve the purpose! danke!

---

