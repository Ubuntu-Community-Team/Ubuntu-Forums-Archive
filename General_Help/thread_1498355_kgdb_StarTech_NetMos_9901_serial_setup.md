---
title: "kgdb StarTech NetMos 9901 serial setup"
date: 2010-05-31
forum: General Help
---

### Post by marc0777 on 2010-05-31
Hi,
I'm running KGDB in the following configuration:

x86_64
Kubuntu 10.04 w/www.kernel.org kernel: linux-2.6.34

A multi-port IO board:  StarTech - 2xSerial + 1xParallel ports
This StarTech board is also known as:  NetMos 9901.  It is a
PCIe board (re: I had no on-board COM port for KGDB). This
board is suppose to configure via kernel/.config - CONFIG_PARPORT_SERIAL.
However, doing a lsmod I only see: 
              serio_raw
              parport_pc   ... ppdev, lp, parport_pc
              re: I do NOT see the NetMos 9901 board/driver .. unless its is hidden?             

kernel command line:   kgdboc=ttyS0,115200 kgdbwait

Boot/debug sequence:
1.  boot up
2.  target/pc stops (re: kgdbwait)
3   Dev-Host/pc connects via gdb, re:
        # gdb ./vmlinux
        (gdb) set remote baud 115200
        (gdb) target remote /dev/ttyS0

        it works...this part works great!

        I can do all kinds of gdb stuff: backtrace, step, next, set/clear breakpoints, etc. 

        but if I ...
4.  (gdb) continue (with no break points set)
     I never can get back into kgdb to do any further debugging.

     For example, doing:
     # echo g>/proc/sysrq-trigger   -- just hangs, gdb does NOT wake up.

     Also, if I set a break point in a driver/module/source (re: mydrv.c) in the 
     module_init code (re: kgdb_breakpoint() ) - this also fails.

Other info:
A.  The 2 serial ports (after I'm booted up) work just fine in user-mode/applications, for example:  minicom -D /dev/ttyS0 -b 115200 (work just fine, as does minicom -D /dev/ttyS1 -b 115200).

I believe the problem is a driver problem (obviously).  But where?
I've been all through the 'setserial' stuff.  I believe I have a baud/rate serial
port configuration (stability) problem (tbd?).

I there anyone out there (kernel/serial-port/guru) who has been through this/similar
with kgdb?  If so I would really appreaciate the help/insight.

thank you in advance.

---

