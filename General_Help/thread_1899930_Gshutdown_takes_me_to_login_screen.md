---
title: "Gshutdown takes me to login screen"
date: 2011-12-24
forum: General Help
---

### Post by leugi101 on 2011-12-24
I have ubuntu 10.04 and i installed gshutdown, but every time i try to shut down my computer with this program it takes me to the login screen, any ideas on what is causing this problem?

---

### Post by c5wagner on 2011-12-24
Try this: go to edit>preferences>actions>custom command>turn off computer, enter '$ sudo shutdown -h now' in the box and hit close.

---

### Post by leugi101 on 2011-12-26
> **c5wagner said:**
> Try this: go to edit>preferences>actions>custom command>turn off computer, enter '$ sudo shutdown -h now' in the box and hit close.here is what worked for me.
I opened the terminal and typed in "sudo chmod +s /sbin/shutdown" then i did as you instructed me except i typed this "shutdown -h now"

---

