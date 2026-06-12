---
title: "Ubuntu Runs &quot;Hotter&quot; Than Windows?"
date: 2012-07-05
forum: General Help
---

### Post by Jeff9 on 2012-07-05
I've noticed that my Lenovo x120e runs about 10*C hotter under Ubuntu (and Xubuntu) than it does under Windows 7. This is even with the same undervolt settings. Is there a reason for this? I experienced the same thing on my old laptop, a Lenovo T61p. 

CPU usage is low...I just don't understand it.

---

### Post by pqwoerituytrueiwoq on 2012-07-05
it is probally the gpu driver
the open source drivers tend to not be very green (energy efficient)

last time i used the official driver on a APU it sucked but this was a desktop APU
but there may be a newer driver out now that does not suck

---

### Post by Jeff9 on 2012-07-05
Thanks for the advice. Unfortunately I just tried that and I didn't make a noticeable difference. Still running warmer than Windows.

---

### Post by Jeff9 on 2012-07-05
Would trying this ([http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)) help? Or is it outdated now with 12.04?

---

### Post by Redblade20XX on 2012-07-05
> **Jeff9 said:**
> Would trying this ([http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)) help? Or is it outdated now with 12.04?

Probably will not work a lot of stuff became depreciated since the 2.X series.

Do you have your cpu scaled? Your cpu maybe set to the max clock rate all the time even though there is little work which drives up heat.

Try jupiter: [http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html#more-13276](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html#more-13276)

Also is this a intel cpu. I heard there were power problems with the kernel for the sandybridge family. I heard its suppose to be resolved in the 3.5 series.

- Red

---

### Post by pqwoerituytrueiwoq on 2012-07-06
> **Redblade20XX said:**
> 
Also is this a intel cpu. I heard there were power problems with the kernel for the sandybridge family. I heard its suppose to be resolved in the 3.5 series.
i looked up the model earlier it is a amd APU 
1.6GHz dual-core AMD Fusion E-350

---

