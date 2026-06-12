---
title: "Need Help with 4 Port PCI RS232 Card"
date: 2010-11-04
forum: General Help
---

### Post by stoynev on 2010-11-04
I need help with 4 Port RS232 PCI Card, I have plugged it to the machine but it seems that when I try to use those ports they don't work, thats what its showing in lspci -v:

> 04:01.0 Serial controller: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 0 (Uart) (prog-if 06)
        Subsystem: Oxford Semiconductor Ltd Device 0000
        Flags: medium devsel, IRQ 19
        I/O ports at d000 [size=32]
        Memory at f4100000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d100 [size=32]
        Memory at f4101000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2
        Kernel driver in use: serial

04:01.1 Bridge: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 1 (8bit bus)
        Subsystem: Oxford Semiconductor Ltd Device 0000
        Flags: medium devsel, IRQ 19
        I/O ports at d200 [size=32]
        Memory at f4102000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d300 [size=32]
        Memory at f4103000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2
        Kernel driver in use: serial

ANy help would be appreciated.

Thank you.

PS: I am using Ubuntu 9.10 ...

---

