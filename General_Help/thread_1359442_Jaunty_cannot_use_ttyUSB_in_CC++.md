---
title: "Jaunty: cannot use ttyUSB in C/C++"
date: 2009-12-19
forum: General Help
---

### Post by meereck on 2009-12-19
Hello,
when I use ttyUSBx with Cutecom, everything works well.
If I create a C or C++ application to read/write ttyUSBx, the port gets open well but nothing can be read from the port. Writing causes garbage on the output.
However, I can see that the port is configured properly (via stty command).

The issue occures with 2.6.30 and 2.6.31. No matter wheter I use USB-RS232 adapter based on FTDI or Prolific chip.
It shall be noted that everything works well if I boot in kernel 2.6.28.

I believe the problem emerged after upgrade from 9.04 to 9.10

Has anyone come across this issue?
cheers Meereck

---

### Post by dcstar on 2009-12-19
> **meereck said:**
> Hello,
when I use ttyUSBx with Cutecom, everything works well.
If I create a C or C++ application to read/write ttyUSBx, the port gets open well but nothing can be read from the port. Writing causes garbage on the output.
However, I can see that the port is configured properly (via stty command).

The issue occures with 2.6.30 and 2.6.31. No matter wheter I use USB-RS232 adapter based on FTDI or Prolific chip.
It shall be noted that everything works well if I boot in kernel 2.6.28.

I believe the problem emerged after upgrade from 9.04 to 9.10

Has anyone come across this issue?
cheers Meereck

The chances that anyone here using that combination of apps - and actually reading this - are tiny.

You should be reporting this to the kernel developers if it seems kernel related.

---

### Post by meereck on 2009-12-20
Right, but it works well on another machine with the same ubuntu and kernel.

I have just discovered a weird thing:
As I previously stated, reading doesnt work, the port is open but no characters are read from the serial port.
Reading in Cutecom works well.

If I open a port in Cutecom and then run my C++ application, the application opens the port, cutecom gets frozen, and application reads date from the port well.
In other words, while cutecom is running and reading the port, reading in C++ application works as well.

cheers

---

