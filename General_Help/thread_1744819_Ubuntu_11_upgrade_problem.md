---
title: "Ubuntu 11 upgrade problem"
date: 2011-04-30
forum: General Help
---

### Post by dlemos on 2011-04-30
Hi all

Could you help me with this issue? I tried to upgrade from 10.10 to Ubuntu 11. The installation was complete but after restarting, I get stuck at a screen with several OK/Fail messages.

All of them turn out OK but one of them "Enabling Automatic Report Crash generation" says FAIL.

So I'm stuck at this scren and can't acces Desktop :(

Thank you

---

### Post by Spyderkid on 2011-04-30
boot into recovery and tell synaptic to do a package check?

---

### Post by Rubi1200 on 2011-04-30
First of all, do NOT do a hard shutdown as you could make things worse.

Do this:

Hold down the Alt and SysRq (Print Screen) keys and slowly type out R E I S U B

this will take the system down safely for reboot.

As the system restarts try what Spyderkid suggested and go into Recovery Mode, choosing the option to repair packages.

This may or may not be the problem, but it is worth trying first.

---

### Post by dlemos on 2011-04-30
Hi guys thanks for the help

Seems the problem was the lack of the graphic card driver. I entered using recovery mode without graphic card, installed the ATI Radeon Driver and then it worked.

I also tried your suggestion. Synaptics says "successfully fixed dependency problems".

Everything seems to be working fine now. Thank you:)

---

### Post by Rubi1200 on 2011-05-01
Excellent! Glad you got things sorted out :-)

---

