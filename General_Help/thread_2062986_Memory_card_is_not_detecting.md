---
title: "Memory card is not detecting"
date: 2012-09-26
forum: General Help
---

### Post by Ramakrishna1 on 2012-09-26
Memory card is not detecting in ubuntu 12.04. How can i solve this problem?

---

### Post by shreepads on 2012-09-26
> **Ramakrishna1 said:**
> Memory card is not detecting in ubuntu 12.04. How can i solve this problem?

Which Ubuntu version?
What hardware setup?
Which memory card?
How is the memory card attached to the computer?
Do you see any errors in /var/log/syslog when you plug in the memory card?

---

### Post by Ramakrishna1 on 2012-09-26
Which Ubuntu version?
Ubuntu 12.04
Which memory card?
sandisk 2GB micro SD
How is the memory card attached to the computer?
Using samsung mobile.
Do you see any errors in /var/log/syslog when you plug in the memory card?
no

---

### Post by shreepads on 2012-09-26
It looks like the problem is that your Samsung mobile (what model and is it plugged in via USB 2.0?) is not getting detected and connected in Ubuntu...

Suggest that you close this thread and start a new one with your mobile name in the subject and include the contents of the command-line output from 'lsusb -v'.

---

