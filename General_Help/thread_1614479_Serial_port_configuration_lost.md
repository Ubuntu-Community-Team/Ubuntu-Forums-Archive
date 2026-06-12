---
title: "Serial port configuration lost"
date: 2010-11-05
forum: General Help
---

### Post by Jim Custy on 2010-11-05
ttyS ports not configured properly anymore.
Something has gone wrong and I do not know how to fix it.

Installed Virtualbox with clients for XP and Ecomstation. (OS/2)

I have a US Robotics Model 5610 56k modem which was on /dev/ttyS1 and seen by OS/2
on COM 2  Port 0x2F8 irq=3  

(XP has no serial port configured in this system)

The host is Ubuntu 10.04 kernel 2.6.32-25-generic; AMD Phenom 925, RAM 3.9GB

All was working fine.   I am not sure why, and it may have been a kernel update that 
caused this:

Standard Ports are no longer recognized.

Here is what I can report:

james@Work64:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    1.018544] 0000:03:07.0: ttyS0 at I/O 0xec00 (irq = 22) is a 16550A
_______________________________________________________________________

james@Work64:~$ setserial -g /dev/ttyS0
/dev/ttyS0, UART: 16550A, Port: 0xec00, IRQ: 22

james@Work64:~$ setserial -g /dev/ttyS1
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3

james@Work64:~$ setserial -g /dev/ttyS2
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
_________________________________________________________________________

james@Work64:~$ cat /var/lib/setserial/autoserial.conf
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use 
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. 
    If you do not do this, this file may be overwritten automatically the 
    next time you upgrade the package.

/dev/ttyS0 uart 16550A port 0xec00 irq 22 baud_base 115200 spd_normal skip_test
james@Work64:~$ 

I am not familiar with 'setserial' and from what I have read I don't think
setserial can fix the standard ports. I hope someone can help me with this.

---

