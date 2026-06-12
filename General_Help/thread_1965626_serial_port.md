---
title: "serial port"
date: 2012-04-26
forum: General Help
---

### Post by balaraja on 2012-04-26
Hi All,

I am using Ubuntu 10.04 on both the machines and I am trying to connect the two machines back to back using serial port for kernel debugging.

But my back to back serial port connection doesnt seem to transfer any data, I checked it using minicom and stty.

I use /dev/ttyS0 and baud rate is 115200.


Here is my dmesg output.
$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    3.970911] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.971182] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.971284] 0000:00:03.3: ttyS1 at I/O 0xecb8 (irq = 17) is a 16550A
$ 

From the output I see ttyS[01] is enabled. But couldnt figure out whey there is no data transfer.

Can anybody help me out. What I am missing here? 

Also is there any other way for back to back connection, like connecting USB ports back to back instead of serial port? 

Thanks in advance!!!

---

### Post by dcstar on 2012-04-27
> **balaraja said:**
> Hi All,

I am using Ubuntu 10.04 on both the machines and I am trying to connect the two machines back to back using serial port for kernel debugging.


Using a null-modem cable?

---

### Post by balaraja on 2012-04-27
Yes sorry I was trying to use console cable instead of null modem cable. 

My bad!! Thanks for your reply.

---

### Post by dcstar on 2012-04-28
> **balaraja said:**
> Yes sorry I was trying to use console cable instead of null modem cable. 

My bad!! Thanks for your reply.

No worries, some of us here are old enough to have used these things in pre-historic times!

I reckon 99% in these forums wouldn't know a DCE from a DTE these days........

---

