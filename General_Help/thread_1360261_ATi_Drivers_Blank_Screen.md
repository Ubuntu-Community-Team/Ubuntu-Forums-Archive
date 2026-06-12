---
title: "ATi Drivers Blank Screen"
date: 2009-12-20
forum: General Help
---

### Post by Ramzy on 2009-12-20
Hi there,

I've got a laptop that i use at work (Toshiba A200). I've installed Ubuntu 9.10 on it, and it works fine.

After installing, i connected it to the net, installed all available updates, and everything ran smoothly.

After that, i attempted to use extra desktop effects (via compiz), and it repeatedly failed. The laptop has an inbuilt ATi 2400, so i figure it should easily handle compiz.

So i jumped into the device manager, and allowed it to download and install the latest ATi drivers. After the drivers installed, i restarted the computer, attempted to boot into Ubuntu, and got nothing but a blank / black screen.

The caps lock key is flashing, and i've left it for 20 minutes, and still nothing.

This is the second time it has happened (decided to test once again just to be sure).

Any suggestions as to why this is happening, and what i can do to get compiz working? I don't mind re-installing Ubuntu once again.

Thanks.

---

### Post by Mark Phelps on 2009-12-21
Compiz is not the problem.  It's most likely a combination of the drivers you installed and the Xorg version in Ubuntu 9.10.

ATI dropped support for all but the latest HD 3x/4x/and 5x cards when they updated drivers for Ubuntu 9.04 and newer.

While your card MIGHT be supported, the results you're getting indicate more likely that it is not.

You can use the link below to remove the ATI drivers and install the open source drivers.  That will not prevent you from using Compiz.

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Ramzy on 2009-12-21
I have not installed any drivers on the computer.

I just formatted it, updated Ubuntu, and i'm currently on the desktop.

Compiz reports that desktop effects can't be enabled, and i don't see any mention of "ATi 2400" in your link... So should i continue?

---

