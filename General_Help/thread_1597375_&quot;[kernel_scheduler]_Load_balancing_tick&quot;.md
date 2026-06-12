---
title: "&quot;[kernel scheduler] Load balancing tick&quot; on Core 2 Duo"
date: 2010-10-15
forum: General Help
---

### Post by inso_741 on 2010-10-15
Has [this bug]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2387479.html") been fixed in the Maverick kernel?

---

### Post by phaedrus54 on 2010-10-25
No.  I'm still seeing lots of interrupts from "[kernel scheduler] Load balancing tick" with Core2Duo Hp Tm2.

Powertop output:

  16.6% (128.2)   [kernel scheduler] Load balancing tick
  10.0% ( 77.0)D  firefox-bin
  11.2% ( 86.8)   [extra timer interrupt]
   6.4% ( 49.1)   [uhci_hcd:usb3, uhci_hcd:usb6] <interrupt>
   6.4% ( 49.1)   USB device  6-2 : USB Receiver (Logitech)
   5.7% ( 44.0)   [TLB shootdowns] <kernel IPI>
   5.1% ( 39.7)   [iwlagn] <interrupt>

---

### Post by inso_741 on 2010-10-25
yeah me too even with my core i7(tested the live version)
anyone knows if they are even working on it??

---

### Post by starfly on 2010-11-12
I dont Think so...

My i5 Processor is affected too. everything is powered down, nicely 9watts... But the Tick Balancing wakeups are horrible... but nothing is investigated yet...

Does anyone know if this is so exissive in Fedora etc ?

---

### Post by inso_741 on 2010-11-13
since its a kernel bug, all distros must be equally affected

---

### Post by kaffelars on 2010-12-03
I experienced this issue, but I got a cooler and more quiet PC using the mainline kernel.
I wrote a quick howto here:
[http://www.bjortvedtdata.net/?p=199]("http://www.bjortvedtdata.net/?p=199")

---

### Post by inso_741 on 2010-12-06
so did they really fixed it in 2.6.36? It doesn't say so in the bug report...
can you post a powertop screenshot??

---

