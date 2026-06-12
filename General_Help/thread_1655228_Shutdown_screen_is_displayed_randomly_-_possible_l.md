---
title: "Shutdown screen is displayed randomly - possible lirc?"
date: 2010-12-29
forum: General Help
---

### Post by neosurya on 2010-12-29
I run Ubuntu 10.04 Lucid Lynx 

The shutdown screen is displayed randomly, and I get the usual options: "Shutdown, Restart, Suspend, Hibernate", with the message" "The system will be shutdown in 60 seconds". The system works normally if I click cancel. This is quite annoying as the screen shows up without any warning. It is not related to idle usage as the screen comes up even while typing.

I have ruled out heating problems (Nothing seems to overheat, all temperatures are normal). Running Memtest overnight reveals no problems with memory. I looked at log files and found that just before the shutdown menu pops up, syslog has an entry related to Pinnacle PCTV. The screen showed up thrice while I was typing this post, and at each time, the log entries were the following: 

Dec 29 21:25:00 komputer kernel: [ 4205.621261] i2c IR (Pinnacle PCTV): unknown key: key=0x35 raw=0x35 down=1
Dec 29 21:25:00 komputer kernel: [ 4205.750020] i2c IR (Pinnacle PCTV): unknown key: key=0x35 raw=0x35 down=0

Dec 29 21:34:41 komputer kernel: [ 4786.541262] i2c IR (Pinnacle PCTV): unknown key: key=0x35 raw=0x35 down=1
Dec 29 21:34:41 komputer kernel: [ 4786.650009] i2c IR (Pinnacle PCTV): unknown key: key=0x35 raw=0x35 down=0

Dec 29 21:35:25 komputer kernel: [ 4830.530769] i2c IR (Pinnacle PCTV): unknown key: key=0x35 raw=0x35 down=1
Dec 29 21:35:25 komputer kernel: [ 4830.661258] i2c IR (Pinnacle PCTV): unknown key: key=0x35 raw=0x35 down=0

I use a PCTV Pro PCI TV, which works perfectly in TV Time. I only use the svideo input of the card, and do not use a remote. I have not connected the supplied IR sensor and also do not have any other IR device connected.

---

