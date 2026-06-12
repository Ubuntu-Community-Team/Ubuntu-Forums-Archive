---
title: "How do I view/edit IDE driver?"
date: 2012-08-20
forum: General Help
---

### Post by urahonky on 2012-08-20
Hello!

I am currently working on getting an FPGA board running with a SATA (running in IDE mode) HDD attached to it. When I run the following command:

```
lspci
```

I see the following show up:

```
02:00.0 IDE interface: Xilinx Corporation Device 6011 (ref ff)
```

Which is the FPGA board. To keep this from being a very long winded post I was wondering if it was possible to view all of the drivers that are currently running in Ubuntu (I'm using 12.04).

When I try lsmod I get a long list of modules but none of them say anything about IDE or PCI. And if I am finally able to view the driver how would I go about recompiling it into Ubuntu so that I could output some debug messages to help me get this FPGA working properly.

Let me know if you need any additional information and thank you for your time!

e: We went ahead and advertised ourselves as an Intel device and it was assigned the PIIX driver. We're going to go ahead and move on from here.

---

### Post by urahonky on 2012-08-20
I see that with lspci -v you can see the drivers that are in use for particular devices... However there isn't a driver given (which I assumed to happen) for my device and I am still unsure how to load a driver for a device.

If I'm in the wrong forum please tell me. :)

---

