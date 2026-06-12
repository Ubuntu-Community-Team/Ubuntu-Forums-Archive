---
title: "Ubuntu 4+ serial ports"
date: 2010-04-27
forum: General Help
---

### Post by sj1410 on 2010-04-27
Hi,

I am using ubuntu 9.04 32 bit desktop and i have onboard 6 RS232 serial ports. i have added the following line to the grub menu.lst to add 4+ serial port support to ubuntu

8250.nr_uarts=6

the problem is that ttyS4 & ttyS5 share IRQ with ttyS1 & ttyS3

root@ubuntu:~# cat /proc/tty/driver/serial 
serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 tx:0 rx:0
1: uart:16550A port:000002F8 irq:11 tx:320 rx:33 RTS|DTR
2: uart:16550A port:000003E8 irq:3 tx:49207 rx:58304 RTS|DTR
3: uart:16550A port:000002E8 irq:10 tx:202 rx:189 brk:1 oe:11 RTS|DTR
4: uart:16550A port:000004F8 irq:11 tx:65 rx:79 RTS|CTS|DTR|DSR|CD|RI
5: uart:16550A port:000004E8 irq:10 tx:186 rx:0 RTS|DTR

this is my setserial config, what irq should i se for S4 & S5, so that it work properly.

root@ubuntu:~# cat /var/lib/setserial/autoserial.conf
/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test
/dev/ttyS1 uart 16550A port 0x02f8 irq 11 baud_base 115200 spd_normal skip_test
/dev/ttyS2 uart 16550A port 0x03e8 irq 3 baud_base 115200 spd_normal skip_test
/dev/ttyS3 uart 16550A port 0x02e8 irq 10 baud_base 115200 spd_normal skip_test
/dev/ttyS4 uart 16550A port 0x04f8 irq 11 baud_base 115200 spd_normal skip_test
/dev/ttyS5 uart 16550A port 0x04e8 irq 10 baud_base 115200 spd_normal skip_test

---

### Post by sj1410 on 2011-01-11
this is bug in ubuntu 9.04. i got no replies for it and the problem does not appear in 10.04.

Thanks

---

### Post by theozzlives on 2011-01-11
> **sj1410 said:**
> this is bug in ubuntu 9.04. i got no replies for it and the problem does not appear in 10.04.

Thanks

9.04 has reached End Of Life.

---

### Post by sj1410 on 2011-01-11
when i enable 6 serial ports in ubuntu 9.04 as mentioned in my original post, i am not able to use the other 2 which shares the same IRQs but have different baud rate.

---

