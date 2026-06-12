---
title: "serial 18250 too much work for irq19"
date: 2010-07-12
forum: General Help
---

### Post by ibrabeicker on 2010-07-12
I installed ubuntu on a relative's computer but on the last moment, before the "restarting now" the screen began to spam this message.

After this everytime the system logs on after 3~10 seconds the graphic interface freezes, so i entered the TTY1 before that, but again the message "serial8250 too much work for irq19" began to spam and obviously this is the cause of the problem

info:
pentium dual core
2GB ram
HDD 300GB
ubuntu 10.04 32-bits

what is thiis and how to fix it??

---

### Post by manofsteel on 2010-07-30
I get the same message, but in Xubuntu, it wont let me log in its so bad. It just kicks me back out to the login screen.

---

### Post by dino99 on 2010-07-30
ive a bios setting about irq19, so check yours or boot with irqpoll on the boot line (hold "shift" key down at end of bios process to see grub menu, then edit (E) the boot line and before "quiet splash" add irqpoll if needed, then boot (ctrl+X))

---

### Post by manofsteel on 2010-07-30
Will try. Thank you so much. :p

---

### Post by manofsteel on 2010-07-30
Tried what you suggested. Tried to log in, it showed me the top task bar, then logged me back out to the commandline for a quick second, showed me two lines. And logged me back out again.

---

