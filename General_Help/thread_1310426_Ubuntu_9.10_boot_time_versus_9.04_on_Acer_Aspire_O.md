---
title: "Ubuntu 9.10 boot time versus 9.04 on Acer Aspire One 8GB SSD"
date: 2009-11-01
forum: General Help
---

### Post by jgolightly on 2009-11-01
One of the biggest "features" listed as part of the 9.10 Karmic release is the reduced boot time in an effort to hit the magic 10 second boot time mark.  Of course, this is in mostly ideal conditions, so I had no expectation that my boot time would come near 10 seconds.  I have, however, seen a drastic INCREASE in the boot time since I installed 9.10.  I'll explain my machine and the boot scenarios:

Acer Aspire One 110 1.6GHz Intel Atom, 1.0 GB RAM
8GB SSD - ext4 filesystem
8GB SDHC - 2GB swap, 6GB FAT

Normal boot times:
Ubuntu 9.04 out of the box: 0 minutes, 50 seconds (GRUB to wifi connect)
Ubuntu 9.10 out of the box: 1 minute, 48 seconds (GRUB to wifi connect)

This is not using autologin, but this is averaged across several boots, including entering my username and password under 9.04 and clicking my username and entering password under 9.10.


Any thoughts on why my boot time may be so much longer in 9.10?

---

### Post by Giblet5 on 2009-11-01
No idea, but 9.10 takes 27 seconds on on this laptop: a Gateway 7811FX with a T9500 CPU mod. Jaunty was slower, for sure, but I don't know how much. I have other things to do than benchmark boot times.

Use bootchart and see where the delay is.

---

### Post by jgolightly on 2009-11-02
Thanks for the quick response.  I'll google bootchart and follow that.  Thanks for the tip.

For whatever reason, I had timed my 9.04 bootup when it was first released to see how ext4 compared to my previous ext2 installations of 8.10.  I would never have given 9.10 a second thought except that it seemed to take quite a bit longer, so I started timing a few boots with that, too.

Thanks again.

---

### Post by blackSP on 2009-11-19
9.10-64 bit booting from intel 80gb postville, /home on 250gb hd, desktop with e7600 core 2 duo en 4gb ram

startup time after bios load: 6 seconds (bios takes about 5)
shutdown time: 3 seconds

---

### Post by Maringouin on 2009-11-22
jgolightly,
I have the same config of netbook that you do, running Kuki at the moment. It looks like you did a complete reinstall, thanks for providing your parameters. Did you have any trouble with wifi, webcam, etc? or did everything work pretty well straight out of the box?
I'm assuming you used the netbook remix version.
Thanks. I'm feeling nervous about upgrading because I don't understand a lot of the code and complaints that are flying around.
Maringouin

---

### Post by Peeved Chemist on 2009-11-23
> **jgolightly said:**
> 
Acer Aspire One 110 1.6GHz Intel Atom, 1.0 GB RAM
8GB SSD

Normal boot times:
Ubuntu 9.04 out of the box: 0 minutes, 50 seconds (GRUB to wifi connect)
Ubuntu 9.10 out of the box: 1 minute, 48 seconds (GRUB to wifi connect)


Are you experiencing this bug?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445852)

If you are, try adding "irqpoll" to your kernel options line in GRUB.  But beware, this bug can corrupt your filesystem.

---

