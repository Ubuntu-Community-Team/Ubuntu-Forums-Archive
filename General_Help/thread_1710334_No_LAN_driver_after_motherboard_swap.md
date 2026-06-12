---
title: "No LAN driver after motherboard swap"
date: 2011-03-19
forum: General Help
---

### Post by Quatrix on 2011-03-19
I just upgraded to an ASUS P8P67 Pro (Sandy Bridge) motherboard and moved my old hard drive to the new case.  Windows 7 and XP are running smoothly.  Ubuntu, however, doesn't detect the Ethernet adapter or doesn't have a suitable driver.  ASUS doesn't offer Linux drivers for this motherboard.  Is there a way to make Ubuntu revert to a default, working driver?

---

### Post by gordintoronto on 2011-03-19
Open Accessories/Terminal and enter this command:
lspci

One of the lines will identify the Ethernet adapter. Then you can Google that ID with "linux."

What version of Ubuntu are you using? You might try making a LiveCD of the Natty daily build, which has a very recent Linux kernel. If that works, you can make a decision about whether you want to wait a month, or use Alpha (testing!) software.

(I'm writing this from Natty, so at some level it works fine.)

---

### Post by Quatrix on 2011-03-29
Resolved, thanks.  Here's what lspci said:

00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1503] (rev 05)

That didn't get me very far, but I searched for the device model (82579V) shown in Windows and came across the e1000e drivers at SourceForge.  "make install" and "modprobe e1000e" got it running.

---

