---
title: "Failed shutdown/reboot in 10.10"
date: 2010-11-23
forum: General Help
---

### Post by timteka on 2010-11-23
Hi, guruz. we've just bought 30 newest nettops ACER Aspire R3700 with ION 2. I've tried ubuntu, kubuntu, xubuntu. Everything works as expected, but... the first one freezes when trying to reboot, shutdown or enter sleep mode. Checked on several hardware units. The desktop just freezes and nothing happens (ubuntu 10.10, both x32 and amd64). Also no one installs the wi-fi drivers, only ethernet  :-(

---

### Post by cariboo on 2010-11-23
I would probably help if you gave us the system specs, including wireless device.

---

### Post by galvatron408 on 2010-11-24
you should also post what the log says. Once you powered the machine back up, look in /var/log/messages and post its contents prior to the freeze. Hopefully, there is something useful there.

---

### Post by nl4m on 2010-11-24
I did not get you. All 30 of your computers work great. Only one has the problem of shutting down? If that's the case it *maybe* have a bad hard drive. Try downloading "hirens boot cd" and doing an HDD test to see if your hard drive is in tip top shape.

---

### Post by asdf29 on 2010-12-18
Dan Wood put a review on Ebuyer with a fix to the wireless issue.  My R3700 is arriving on Monday so not sure if it works yet.  Looks like a good deal at £199.

> 
Open a terminal and type:
sudo pico /etc/modprobe.d/blacklist.conf

Now add this to the bottom of the file:
blacklist rt2800pci

Save the file (Ctrl+o)

Now reboot (you'll still need to hold power button in this time!).

[http://www.ebuyer.com/product/236579]("http://www.ebuyer.com/product/236579")

---

