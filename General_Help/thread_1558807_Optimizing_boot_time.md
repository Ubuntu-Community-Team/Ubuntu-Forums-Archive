---
title: "Optimizing boot time"
date: 2010-08-22
forum: General Help
---

### Post by jbdutton on 2010-08-22
Hi,
I've been trying to chip away at my laptop's boot time, as its battery is dead in the permanent sense and I must shutdown and boot up whenever it is moved. Right now, a cold boot to the login window is around 40 seconds (which is probably reasonable, but making it shorter can't hurt), so any tips on making it faster would be appreciated!

My laptop is an HP Pavilion dv7 with 4gb of RAM and the AMD Turion X2 duel-core processor, with the following partitions:
Extended 180GB for Ubuntu 10.04, with 7.3GB as swap space,
12GB as the HP_RECOVERY partition,
31GB for Windows Vista (unused, but I may need it down the road),
and 27GB for Jolicloud, for no real reason.

Although my bootchart clocks in at twenty-three seconds (attached), in reality it takes ten seconds for the HP logo to appear, and another thirty for the login window. I've already tried removing unnecessary services, disabling the floppy boot check, and switched from bash to dash. I can upload my dmesg output if needed.

Regards,
jbdutton

Edit: [Bootchart at imageshack]("http://img837.imageshack.us/img837/4629/terminuslucid2010082210.png")

---

