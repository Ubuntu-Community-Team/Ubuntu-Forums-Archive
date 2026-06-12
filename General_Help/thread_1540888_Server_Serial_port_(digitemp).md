---
title: "Server Serial port (digitemp)"
date: 2010-07-28
forum: General Help
---

### Post by Grenage on 2010-07-28
On a 10.04 server install, I'm having issues reading a temperature array using digitemp:

The array works fine on Windows servers.
The array works on Ubuntu servers **only** if I add a separate serial card.

Unfortunately, I cannot add another serial card to this server; it's a 1U rack-mount.  I've never been able to poll the array when using a 9.10 or 10.04 server using the on-board port; so I've come to the conclusion that the port is being used differently to how it would be used in Windows.  It could be drivers, I haven't got a clue.

Does anyone know if there are settings that can be toyed with for the serial ports, within Linux?

---

### Post by Grenage on 2010-07-30
Marking this as solved; not because it is, but because I'm not sure it's Ubuntu that's the problem.  The same problem occurred on a Debian live CD, and I'm suspecting that the on-board serial port is just not supplying enough power.

Worked around with a serial card... and a hacksaw.

---

