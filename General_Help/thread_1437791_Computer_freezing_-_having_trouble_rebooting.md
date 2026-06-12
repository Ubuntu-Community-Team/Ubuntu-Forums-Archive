---
title: "Computer freezing - having trouble rebooting"
date: 2010-03-24
forum: General Help
---

### Post by Mickeylyn on 2010-03-24
I am new to linux and have Ubuntu 8.04 and Windows XP on my desktop (Intel Pentium dual processor).

In windows twice and now Ubuntu once, my computer has frozen and I had to turn it off. When I try to it back on, I get the message "Disk boot failure, Boot from CD." 

This is a problem I had before reformatting the hard drive and installing ubuntu. At that time I would insert the Windows XP disk and it would tell me It could not detect the hard drive, but I could then restart the computer and it would work for awhile before freezing again. Eventually, however nothing worked.

This time when I get the boot failure message I turn the computer off and back on again and it works after the 3rd or 4th time. 

When this happen the first time (on windows) I had a flash drive plugged in that I thought might be the cause (virus maybe?). I haven't used the flashdrive or windows since this started.

The computer was built from scratch by a family member. Could it be a hardware issue?

Any help would be great.
Thanks,
Mickeylyn

---

### Post by audiomick on 2010-03-24
the first suspicion would be a drive problem. I would run "smartmontools" on it. You can read about that here
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

The other thing (to do first) is open the case and make sure all the cables are plugged in properly. It is not a bad idea to pull the plug out a couple of times to make sure the connector has not become oxidised. If the cables are stiff like my SATA cables are, make sure they are not putting the connector under stress.

---

