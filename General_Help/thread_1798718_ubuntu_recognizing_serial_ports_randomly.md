---
title: "ubuntu recognizing serial ports randomly"
date: 2011-07-06
forum: General Help
---

### Post by just_abhi22 on 2011-07-06
hi all
i am facing a unique problem.
i ahd installed ubuntu in vmware.whenever i try  doing

[abhi@localhost ~]$ dmesg | grep tty
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

i end up having this message. i have not initialized any serial port in vmware still i am having this message.even if i initialize serial port in vmware,it does not show up here.
the result remains the same.

how could i see my initialized serial port?this problem does not happen when i do so in ubuntu installed in separate partition. how to solve this issue??

please address this as soon as possible.

any help regarding would be appreciable.



abhishek

---

