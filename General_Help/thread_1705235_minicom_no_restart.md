---
title: "minicom no restart"
date: 2011-03-11
forum: General Help
---

### Post by Don DeGregori on 2011-03-11
[I]Intalled minicom. Want to use it with MCP2200 UART to USB chip.
Microchip suggests this procedure for Linux
I do all this as regular user and it works:[/I]

[B]lsmod | grep cdc
dmesg | grep ttyACM
ls /dev/ttyACM*
ln -sf /dev/ttyACM0 /devUSB0
stty -F /devUSB0 57600[/B]

[I]Then, I execute minicom in terminal.
minicom comes up fine and I see my data.
If I close minicom and restart, no problem.
But, if I shut down Ubuntu and restart, or pull
USB cable and reinsert, minicom will not start.
I find I have to put in the ln command again.
Then it works. I notice in /dev, the USB0 and ACM0
are owned by root.
Don[/I]

---

