---
title: "setting up printer. (stuck)"
date: 2010-06-19
forum: General Help
---

### Post by GreatKeyHunter on 2010-06-19
I need a little help setting up my printer.  every time i try, it says, there was an error during cups operation: ' failed to connect to server'  other than that i ran this on the terminal and got this information back.

greatwhite@greatwhite:~$ $ lsmod | grep lp
$: command not found
greatwhite@greatwhite:~$ lsmod | grep lp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
greatwhite@greatwhite:~$ lsmod | grep ppdev
ppdev                   5259  0 
parport                32635  3 ppdev,parport_pc,lp
greatwhite@greatwhite:~$ lsmod | grep parport_pc
parport_pc             26250  1 
parport                32635  3 ppdev,parport_pc,lp
greatwhite@greatwhite:~$ dmesg | grep par
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.291055] pci 0000:00:1e.0: transparent bridge
[    0.481243] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.585074] eth0: Tigon3 [partno(BCM95705A50) rev 3003] (PCI:33MHz:32-bit) MAC address 00:0d:60:dd:12:12
[   12.957253] parport_pc 00:0c: reported by Plug and Play ACPI
[   12.957377] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   13.000034] parport0: Printer, Dell Dell Laser Printer 1700
[   13.000486] lp0: using parport0 (interrupt-driven).
[   14.766337] ppdev: user-space parallel port driver
[12695.308649] UDF-fs: No partition found (1)
greatwhite@greatwhite:~$ lpinfo -v
lpinfo: Connection refused
greatwhite@greatwhite:~$ lpinfo - v
lpinfo: Unknown option 'greatwhite@greatwhite:~$ 
greatwhite@greatwhite:~$ lpinfo -v
lpinfo: Connection refused

any suggestions will be highly appreciated.

---

### Post by Dimarchi on 2010-06-19
My search on the issue yields the following link:

[http://blog.astradele.com/2008/06/12/getting-dell-1700-laser-printer-working-on-ubuntu-linux/](http://blog.astradele.com/2008/06/12/getting-dell-1700-laser-printer-working-on-ubuntu-linux/)

which in turns links to:

[http://www.linuxquestions.org/hcl/showproduct.php/product/2463/sl/1](http://www.linuxquestions.org/hcl/showproduct.php/product/2463/sl/1)

Do you see the printer coming up (System > Administration > Printing)? Or, guesstimating, is there anything at lpr://dev/lp0 or lpd://dev/lp0? What type of connection do you use? Parallel, if I read that report correctly?

---

### Post by GreatKeyHunter on 2010-06-19
> **Dimarchi said:**
> My search on the issue yields the following link:

[http://blog.astradele.com/2008/06/12/getting-dell-1700-laser-printer-working-on-ubuntu-linux/](http://blog.astradele.com/2008/06/12/getting-dell-1700-laser-printer-working-on-ubuntu-linux/)

which in turns links to:

[http://www.linuxquestions.org/hcl/showproduct.php/product/2463/sl/1](http://www.linuxquestions.org/hcl/showproduct.php/product/2463/sl/1)

Do you see the printer coming up (System > Administration > Printing)? Or, guesstimating, is there anything at lpr://dev/lp0 or lpd://dev/lp0? What type of connection do you use? Parallel, if I read that report correctly?

parallel.

---

### Post by dino99 on 2010-06-19
you need these packages installed:

[http://packages.ubuntu.com/en/lucid/parport-modules-2.6.32-21-generic-di](http://packages.ubuntu.com/en/lucid/parport-modules-2.6.32-21-generic-di)
[http://packages.ubuntu.com/en/lucid/plip-modules-2.6.32-21-generic-di](http://packages.ubuntu.com/en/lucid/plip-modules-2.6.32-21-generic-di)

---

### Post by GreatKeyHunter on 2010-06-20
thanks everyone i got my printer to work. ty for the support

---

