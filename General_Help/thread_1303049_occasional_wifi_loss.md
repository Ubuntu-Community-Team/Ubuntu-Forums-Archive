---
title: "occasional wifi loss"
date: 2009-10-27
forum: General Help
---

### Post by kammce on 2009-10-27
Not to sure where to put this thread.

On occasion, my computer (running : Ubunut hardy and KDE Desktop) will chose to take a longer time to boot up. After a while of waiting the Kubuntu boot up progress bar screen will disappeared and show the command-line and all the process that are booting up. This happens about 30% into the progress bar. The boot up stops at "Configuring Network Interfaces." I would press Ctrl-Alt-Del to skip that process then it will continue its boot up. This is the only process that does this. After having to skip this process and logging in, I find that my Internet doesn't work. I check "iwconfig" and "ifconfig" and it only shows "lo" and "eth0." "Wlan0" is gone. This only happens a few times each week. The only way I know how to get the wifi to show up is to restart or to use "sudo modprobe ndiswrapper".

I am using ndiswrapper to emulate x64 netgear WG311v3 drivers for my netgear WG311v3 wifi PCI card.

With a normal boot-up "Wlan0" shows up. I don't know if its because I use ndiswrapper, I didn't install the emulate into the kernel correctly.
Please help

---

### Post by sailthesea on 2009-10-27
I had a similar problem with Hardy I believe the kernel/ndswrapper config wouldn't start properly now and then It was way better with Intrepid and out of the box with Jaunty
 Try Jaunty perhaps? Mint is also very good
Good luck!

---

### Post by kammce on 2009-10-27
Thanks. When I have 5 hours to spare then I will try upgrading to jaunty.

---

### Post by sailthesea on 2009-10-27
> **kammce said:**
> Thanks. When I have 5 hours to spare then I will try upgrading to jaunty.
:p
 If you can, burn a Jaunty LiveCD and try it out. If you all goes well you can upgrade or install from that. The jippy wireless is a pain, but nothing compared to upgrading through two releases on a dodgy connection! 
 Bottom line is: the support for Netgear is much better in Jaunty

---

### Post by kammce on 2009-10-27
Thanks alot for your advice

---

