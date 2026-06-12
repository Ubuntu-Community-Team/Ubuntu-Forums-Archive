---
title: "COM Port(RS232) issue"
date: 2011-03-15
forum: General Help
---

### Post by gerardjohn on 2011-03-15
I installed Ubuntu 10.04 LTS on my Intel atom PC;the PC came with one(1) on-board COM port(RS232)and I used a PCI Serial card supporting two(2) COM ports(RS232). I am able to send an receive data from the on-board COM port(ttyS0)whereas the other two COM ports (from the PCI serial card/add-on board) are able to receive but not able to send data. Their I/O address are 0X1000 & 0X1008 and have the same IRQ; IRQ=20; read in some thread in the ubuntu forum that the addresses greater than 0X1000 does not work! How can I change the I/O address, IRQ values? :confused:

---

