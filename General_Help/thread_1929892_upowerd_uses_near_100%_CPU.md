---
title: "upowerd uses near 100% CPU"
date: 2012-02-22
forum: General Help
---

### Post by laurian on 2012-02-22
Hi,
I updated a few days ago and since then, I noticed my computer is much slower. top tells me that upowerd uses almost 100% of my CPU. Amongst the recent updates is kernel 3.0.16.
I am using Ubuntu 11.10, gnome shell 3.2.1, upower --version gives "UPower client version 0.9.13" and "UPower daemon version (null)". My computer is a eee 1005P. Google was not very helpful although i noticed people talked about acpi. I have some Linux knownledge but I'm no guru either.

Thanks for any help!

-- Laurian

---

### Post by Damascushead on 2012-02-22
In the terminal use the ```
ps
``` command to see a list of running processes.

Or use ```
ps -A
``` to see a list of all running processes. This might let you know what processes are running and perhaps taking up the most processing power.

The "System Monitor" tool is also good to see which processes are using the most CPU.

Hope this helps:D

---

### Post by laurian on 2012-02-24
Well I was using top which was telling me that upowerd was using 98% of my CPU... Thanks anyway.

---

