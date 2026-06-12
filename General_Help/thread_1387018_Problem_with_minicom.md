---
title: "Problem with minicom"
date: 2010-01-21
forum: General Help
---

### Post by venky485 on 2010-01-21
In winxp I have installed vmware and then ubuntu 8.1 in vmware. 
My serial port is detected as com2 in winxp and my ARM board's serial output is printed properly on the Hyperterminal. It works fine in winxp. 
I installed minicom in Ubuntu and set the baudrate to 115200N1. I set the /dev/ttyS0 and also /dev/ttyS1.
But, I do not see any output on the minicom terminal in ubuntu.
Anyhelp is highly appreciated.

this is the dmesg output.
venky@venky-desktop:~$ dmesg| grep tty
[    0.004000] console [tty0] enabled
[    1.620173] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.620532] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.621359] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.621734] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

---

### Post by HermanAB on 2010-01-21
Howdy,

You probably need to turn flow control off.

I'd recommend that you install Cutecom, it works way better than Minicom.

---

### Post by venky485 on 2010-01-21
Thanks for your suggestion. I will try cutecom.
I did the flowcontrol off also in minicom. but, no luck :-(

---

### Post by dominosrob on 2010-01-21
make sure you are mapping COM2 to a device in the VMware settings.

---

