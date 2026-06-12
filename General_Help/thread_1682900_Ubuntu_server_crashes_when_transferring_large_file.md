---
title: "Ubuntu server crashes when transferring large files"
date: 2011-02-06
forum: General Help
---

### Post by Roofle on 2011-02-06
Every time I attempt to transfer over a large file (4 GB) via any protocol, my server restarts.  On the rare occasion that it doesn't restart, it spits out a few error messages saying "local_softirq_pending 08" and then promptly freezes.  Small files transfer fine.

I'm pretty new to Ubuntu server, so what log files would be relevant to help me figure out what's going on here?

Relevant information:
Ubuntu server 10.10
Four hard drives in RAID 5 configuration
CPU/HD temperatures are within normal range

---

### Post by sanderj on 2011-02-06
Googling for it, it looks to me it's network card related.

So, what kind of network card do you use?
And is it possible for you to use another type of network card to see if the problem goes away?

---

### Post by Roofle on 2011-02-06
Using another network card seems to have fixed it.  Unfortunately, the onboard LAN (the one that doesn't work) seems to transfer ~15 MB/s faster than the PCI one I installed (despite both being gigabit).  

Oh well, thanks for the advice!

---

### Post by sanderj on 2011-02-06
> **Roofle said:**
> Using another network card seems to have fixed it.  Unfortunately, the onboard LAN (the one that doesn't work) seems to transfer ~15 MB/s faster than the PCI one I installed (despite both being gigabit).  

Oh well, thanks for the advice!

OK, good for you.

For the record: which brand/type is the problematic network card? Post the relevant output of 'lspci' so that others know about it.

---

### Post by Roofle on 2011-02-06
The problematic card is the onboard gigabit NIC on a Gigabyte GA-H55M-S2V.

From lspci:
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

---

### Post by pnorman on 2011-02-12
I get the same problems with my server
lspci:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


I'm going to be picking up an ethernet card tomorrow. The current controller is the onboard from a Biostar AMD motherboard.

---

### Post by dcstar on 2011-02-12
> **pnorman said:**
> I get the same problems with my server
lspci:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


I'm going to be picking up an ethernet card tomorrow. The current controller is the onboard from a Biostar AMD motherboard.

One of you should be reporting this as a kernel bug, otherwise it may **never** get fixed.

---

### Post by sanderj on 2011-02-12
> **dcstar said:**
> One of you should be reporting this as a kernel bug, otherwise it may **never** get fixed.

My advice: also use Natty Alpha 2 ([http://cdimage.ubuntu.com/releases/natty/alpha-2/](http://cdimage.ubuntu.com/releases/natty/alpha-2/)) from a live-CD or live-USB to see if it has been solved already. 
If so, it's easier to reference to, and easier to backport it to 10.04 and 10.10

---

