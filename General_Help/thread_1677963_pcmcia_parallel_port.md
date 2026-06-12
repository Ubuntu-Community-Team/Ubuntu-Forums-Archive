---
title: "pcmcia parallel port"
date: 2011-01-29
forum: General Help
---

### Post by brandonhon on 2011-01-29
i am tying to get a startech pcmcia parallel port working on my laptop and i just can't seem to get it going. here is my lcpci -v info on the card.
```

07:00.0 Serial controller: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 0 (Disabled) (rev 01) (prog-if 06)
	Subsystem: Oxford Semiconductor Ltd Device 0000
	Flags: medium devsel, IRQ 20
	I/O ports at 4020 [size=8]
	I/O ports at 4028 [size=8]
	I/O ports at 4030 [size=8]
	I/O ports at 4038 [size=8]
	I/O ports at 4000 [size=32]
	Memory at 2c000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: serial

07:00.1 Non-VGA unclassified device: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 1 (parallel port) (rev 01)
	Subsystem: Oxford Semiconductor Ltd Device 0000
	Flags: medium devsel, IRQ 20
	I/O ports at <unassigned> [disabled]
	I/O ports at <unassigned> [disabled]
	I/O ports at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel modules: parport_pc

```

i do not know why it is not assigning it an io address. any suggestions?

i should also add that the parallel port is enable in the bios with the default address of 0x0378. i have also tried modprobe parport parport_pc and parport_cs and ppdev, still nothing. please help me...

---

### Post by brandonhon on 2011-01-29
does anyone know why it says:

```
I/O ports at <unassigned> [disabled]
```

i really need this to work for my cnc machine. i have tried google my a$$ off but have found no solutions.

---

