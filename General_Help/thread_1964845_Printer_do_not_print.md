---
title: "Printer do not print"
date: 2012-04-24
forum: General Help
---

### Post by rdourado on 2012-04-24
Tried to install a Lexmark X2690 on Ubuntu 11.10 64bits, but it is not working.
The current status of the printer is:
Idle - "File "/usr/local/lexmark/lxk08/bin/printdriver" has insecure permissions (0100775/uid=0/gid=2)."

---

### Post by wojox on 2012-04-24
Did you try again from the terminal:
```
sudo chmod 755 /usr/local/lexmark/lxk08/bin/printdriver
```

---

