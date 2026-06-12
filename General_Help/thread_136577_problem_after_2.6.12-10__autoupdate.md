---
title: "problem after 2.6.12-10  autoupdate"
date: 2006-02-26
forum: General Help
---

### Post by vph on 2006-02-26
Hi,
I have a Compaq R3000 with amd64 and Ubuntu 5.10 64bit. Current kernel is 2.6.12-9-amd64-generic. Recently the Autoupdate Manager asked me to update the kernel to 2.6.12-10-amd64-generic. I did it and my wireless adapter (BCM4306 802.11b/g Wireless LAN Controller (rev 03)) disappeared. When booting the old 2.6.12-9... kernel everything is working fine.

Any ideas how to fix the problem?

Best Regards,

Filip

---

### Post by huckem on 2006-02-26
were you using Ndiswrapper on that before?

---

### Post by vph on 2006-02-26
Thankk you for replying.
Yes, I use ndiswraper. I installed it some time ago. It wasn't very straight forward process and I don't want to repeat it if possible. This is why I work now with the old kernel.

Regards,
Filip

---

### Post by mpineiro on 2006-03-23
Yeah getting ndiswrapper working with the R3000 is not a fun time. I had to fight with my machine. Anyway, it sounds like the problem is that by installing the new kernel, you have to compile ndiswrapper again for the new kernel since it's dependent on the kernel version you compiled it on.

I'm not 100% sure though so feel free to correct me.

---

