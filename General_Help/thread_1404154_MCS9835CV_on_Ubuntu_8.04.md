---
title: "MCS9835CV on Ubuntu 8.04"
date: 2010-02-11
forum: General Help
---

### Post by LeMeShiaS on 2010-02-11
Hi I have 2 x MCS9835CV Serial cards on my pc...
The first is working very good ... 
On the second i can not find the /dev/ttyS...

here is  
ls /dev/ttyS*
--------------
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3

ttyS0 = is on mainboard (working)
ttyS1,ttyS2 = is on one pc card (working)
ttyS3 = i dont know what is it !!

here is 
lspci -v
-----------
00:09.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)
        Subsystem: LSI Logic / Symbios Logic Device 0012
        Flags: medium devsel, IRQ 17
        I/O ports at b400 [size=8]
        I/O ports at b000 [size=8]
        I/O ports at a800 [size=8]
        I/O ports at a400 [size=8]
        I/O ports at a000 [size=8]
        I/O ports at 9800 [size=16]
        Kernel driver in use: parport_serial
        Kernel modules: parport_serial

00:0a.0 Serial controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01) (prog-if 02)
        Subsystem: LSI Logic / Symbios Logic Device 0002
        Flags: medium devsel, IRQ 18
        I/O ports at 9400 [size=8]
        I/O ports at 9000 [size=8]
        I/O ports at 8800 [size=8]
        I/O ports at 8400 [size=8]
        I/O ports at 8000 [size=8]
        I/O ports at 7800 [size=16]
        Kernel driver in use: serial
        Kernel modules: parport_serial


dmesg | grep ttyS
--------------------
[    1.630119] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.630361] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.630520] 0000:00:0a.0: ttyS1 at I/O 0x9400 (irq = 18) is a 16550A
[    1.630591] 0000:00:0a.0: ttyS2 at I/O 0x9000 (irq = 18) is a 16550A
[    7.380241] 0000:00:09.0: ttyS3 at I/O 0xb400 (irq = 17) is a 16550A

Can anyone help me ??? PLEASE !!

---

