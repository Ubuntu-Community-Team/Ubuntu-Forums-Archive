---
title: "PCI 232 (DB9 Serial) Card doesn't work"
date: 2012-07-08
forum: General Help
---

### Post by Berenjeno on 2012-07-08
Hi
the PC have 2 port 232 in use and I install a PCI 232 Db9 with 2 Port Serial, So I can have 4 232 port in use and install the Driver, but the problem is that Im trying to use one of the port and doesn't work
:confused:, a friend told me that I have to edit something on the comm port but I cant find it or is any other way so I can put to work this pci 232 to work.

I put this command to verify: setserial -g /dev/ttyS[0123]
and get this[FONT=monospace]
[/FONT]/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4 
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3 
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
 /dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

other comand: dmesg | grep tty
and get this

[   0.001109] console [ttyS0] enabled
[   1.628939] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   1.629033] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   1.629676] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   1.629513] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 

Please some one can help me to put this 2 Db9 serial 232 to work.
thanks!!

---

