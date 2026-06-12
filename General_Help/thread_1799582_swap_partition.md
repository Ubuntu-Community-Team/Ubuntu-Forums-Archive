---
title: "swap partition"
date: 2011-07-07
forum: General Help
---

### Post by Alan.Brown on 2011-07-07
I am running Ubuntu 11.04 on a computer with 2GB RAM.   It seems that it never uses more than about 20-25% of the total RAM even if I have several applications running.

The question is - do I really need to have a swap partition if it is not being used?

Any opinions?

TIA

Alan

---

### Post by wildmanne39 on 2011-07-07
> **Alan.Brown said:**
> I am running Ubuntu 11.04 on a computer with 2GB RAM.   It seems that it never uses more than about 20-25% of the total RAM even if I have several applications running.

The question is - do I really need to have a swap partition if it is not being used?

Any opinions?

TIA

AlanHi, if it is not being used, the only thing you need it for is to suspend or hibernate your system.

---

### Post by searchfgold6789 on 2011-07-07
No, you don't need one, but I am aware of some applications (like Bleachbit) that run exclusively from the Swap area and they might get messed up. I am annoyed by it taking up much disk space, so I just shortened it to 1 gigabyte and I get by just fine. You can also put a small Swap partition on a USB thumb drive and it will be automatically detected and put on when the computer boots, with the 'swapon' command.

---

### Post by Alan.Brown on 2011-07-08
Thanks for your replies.   I am not short of space on the Hard Disk so I will leave the swap partition on it.   The question was academic really.

Thanks

Alan

---

### Post by deserthowler on 2011-07-08
It won't hurt.  Most machines are really over-disked to the point that a GB or so of swap is insignificant.  If you run several programs during a session you might want to run 
```
free -m
```
from a terminal to see how memory you are using and how close to the limit you are.  Run it just before shutting down.  If you run System Monitor you will get readings that are 'false'.

When I began using Linux (Debian Sarge?), I ran a Sparc 64 with 1 GB memory and two 4 GB SCSI hard drives as a desktop machine.  I ran no swap.  I found myself rebooting almost every week.

Earl

---

### Post by bodhi.zazen on 2011-07-08
> **Alan.Brown said:**
> Thanks for your replies.   I am not short of space on the Hard Disk so I will leave the swap partition on it.   The question was academic really.

Thanks

Alan

It depends on what you use your machine for and how much RAM you have.

The average desktop user with more then 2-3 Gb RAM will not use swap.

You will need swap if you use :

hibernation
Applications that want a lot of ram, virtualization and burning DVD are two that come to mind.

---

