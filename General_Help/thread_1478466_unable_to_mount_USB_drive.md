---
title: "unable to mount USB drive"
date: 2010-05-09
forum: General Help
---

### Post by rmcellig on 2010-05-09
I just backed up my internal HD to my external USB drive using Clonzilla. When I restart my computer, I don't see my USB drive on the desktop so I unplugged/replugged my USB drive and received the attached error. What should I do?

---

### Post by garvinrick4 on 2010-05-09
sudo mkdir /media/RADIO2

sudo mount /dev/sdyx /media/RADIO2


y and x being your partition #'s for RADIO2 such as sda1, sdb1, sdc1, ect. ect. ect.


sudo umount /media/RADIO2    (to unmount, not a typo)

---

### Post by rmcellig on 2010-05-09
Thanks garvinrick4!! I will give that a try. How can I find out what my partition# is for my external USB drive if I can't see the drive on my desktop? Is there a network tool (GUI) I can use that will list this info for all of my drives?

---

### Post by rmcellig on 2010-05-09
Everything is fine now. Thanks. Case closed.

---

