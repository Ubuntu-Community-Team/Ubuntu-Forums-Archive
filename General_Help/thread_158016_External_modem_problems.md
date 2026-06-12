---
title: "External modem problems"
date: 2006-04-10
forum: General Help
---

### Post by mikef on 2006-04-10
I'm running Ubuntu 5.10 and am trying to get a US robotics hardware modem to work. The motherboard didn't come with any serial ports, so I added a PCI controller in and the system recognized it. But when I attached the modem it wouldn't initialize. I've tested the modem on another Ubuntu machine, and know it works with the distro, so does anybody have any ideas?

---

### Post by mikef on 2006-04-10
Also, now I'm having trouble with a PCI winmodem that I have installed in it for the windows side of a dual boot system. The modem works fine in windows, so I thought to try using the serial port on it in ubuntu. The problem now is that ubuntu will recognize it, but as long as the modem is installed, it won't connect to my lan, and I need both to work for what I'm doing. I guess its a resource conflict, but I can't find it. I'm new to linux, so I don't know what other info might be needed, so just let me know what, and I'll supply it. Thanks in advance.

---

### Post by bluetoad on 2006-04-10
[QUOTE=mikef]I'm running Ubuntu 5.10 and am trying to get a US robotics hardware modem to work. The motherboard didn't come with any serial ports, so I added a PCI controller in and the system recognized it. But when I attached the modem it wouldn't initialize. I've tested the modem on another Ubuntu machine, and know it works with the distro, so does anybody have any ideas?[/QUOTE]

Take a look at /var/log/dmesg to see which ports have been setup.  Look for entries like

[4294673.698000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294673.700000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

and

[4294673.700000] ttyS14 at I/O 0xbc00 (irq = 21) is a 16550A
[4294673.700000] ttyS15 at I/O 0xb800 (irq = 21) is a 16550A

I put an extra serial card in and it used ttyS14

---

### Post by brentroos on 2006-04-10
*

---

### Post by mikef on 2006-04-11
I'm not actually trying to use the winmodem to connect, I've got an external modem connected to the serial port on the modem. Ubuntu will recognize the port, but if the modem is even in the slot, it blocks my LAN connection. That's my main problem now, is how to connect to the network while the modem is installed, so I can use the serial port on it. Thanks for the replies.

---

### Post by brentroos on 2006-04-12
*

---

