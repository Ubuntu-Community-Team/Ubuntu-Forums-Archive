---
title: "Console via PCI Card Fails to Boot"
date: 2012-02-28
forum: General Help
---

### Post by gdeeble on 2012-02-28
Hey guys,
 I hope someone can point me in the right direction here, but I'm trying to get a console feed from my server and it keeps freezing on the boot if I enable it to look at any port from my PCI card. I followed the [Serial Console How to]("https://help.ubuntu.com/community/SerialConsoleHowto"), which on my old board worked awesome. The new board seems not to like the serial port what so ever, so I grabbed a PCI Serial card to do this. Every time I point to a port on the card during boot, it locks and hangs at ```
ttySx: detected caps 00000700 should be 00000100
```. I put x as I've tried multiple configurations, including on-board off and at other ports. Anytime directed to the card on either port A or B it breaks the boot. The card is a "SIIG Cyber Pro?" as it reads on the label. If anyone can direct me in the right direction so I can get my console connection back(I use it via a make shift Console Server so I can monitor the server if I have to take it down and restart it), I'd be very appreciative. Thanks in advance.

Gary

---

### Post by gdeeble on 2012-02-28
My dmesg | grep ttyS shows the following, if this helps.

```


[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=00dfdc6a-de9e-4dc9-a089-8b1458300c7d ro console=tty0 console=ttyS0,115200n8
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=00dfdc6a-de9e-4dc9-a089-8b1458300c7d ro console=tty0 console=ttyS0,115200n8
[    0.000000] console [ttyS0] enabled
[    2.874831] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.881083] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.893868] ttyS1: detected caps 00000700 should be 00000100
[    2.899548] 0000:03:05.0: ttyS1 at I/O 0xec00 (irq = 20) is a 16C950/954
[    2.906379] ttyS2: detected caps 00000700 should be 00000100
[    2.912075] 0000:03:05.0: ttyS2 at I/O 0xec08 (irq = 20) is a 16C950/954


```

---

### Post by gdeeble on 2012-02-29
Did I post this in the wrong category or something or is this just an off the wall issue that I have?

---

