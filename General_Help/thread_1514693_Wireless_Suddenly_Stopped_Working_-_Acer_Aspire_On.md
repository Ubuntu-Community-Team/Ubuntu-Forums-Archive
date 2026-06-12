---
title: "Wireless Suddenly Stopped Working - Acer Aspire One - Lucid Lynx"
date: 2010-06-21
forum: General Help
---

### Post by libertythor on 2010-06-21
Suddenly after almost 6 months of using Ubuntu, including 2 months on Lucid Lynx my wireless card stopped working.  I have searched previous threads, and the solutions don't seem to work.   I have never had problems with my wireless before.

---

### Post by gkumar on 2010-06-21
I have an Acer Aspire One ZG5 running Lucid Lynx Desktop, so perhaps I can help.

First of all, you'll want to check the wireless switch. I've found that it's a very, very finicky switch, and may require several pushes to activate, and it doesn't work very well to turn the radio back on while booted into Ubuntu. In addition, it's a hardware switch, not a software one, so Ubuntu won't be able to tell the difference between no networks around and the radio turned off. So keep those things in mind.

I usually boot into my Windows installation on my netbook to turn the wifi switch back on if I ever accidentally turn it off. However, if that doesn't work, or if you don't have the ability to connect even on Windows, then it could be a hardware issue.

If, however, you can connect on any other OSs, you probably have a problem with Ubuntu itself. Let me know if you have the option to try any of the above fixes.

If you don't have the ability to boot into Windows, then try booting into a Lucid image from a USB drive (Like how you probably had to to install Lucid in the first place), and checking to see if the liveUSB drive can detect and get your network up and running. If I recall correctly, the LiveUSB drive had my wifi up and running with zero configuration.

Good luck, and let me know how things go.

---

### Post by libertythor on 2010-06-21
It turns out that I was able to kind of force it to work by selecting "connect to a hidden wireless network" and then selecting my network on the dropdown in that.   Of course it failed to connect, but the wireless indicator light started flashing.   I then rebooted the laptop, and everything was working fine.

---

### Post by gkumar on 2010-06-22
Wow, that's really weird. Glad to hear it's working now, though.

---

### Post by kamicc on 2010-12-12
Got same problem with Toashiba A300-20N and same 10.04.
Found this one [https://bugs.launchpad.net/ubuntu/+bug/132042](https://bugs.launchpad.net/ubuntu/+bug/132042)
active problem since... 2007 :O

---

