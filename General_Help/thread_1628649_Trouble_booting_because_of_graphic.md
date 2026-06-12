---
title: "Trouble booting because of graphic"
date: 2010-11-22
forum: General Help
---

### Post by atonal on 2010-11-22
I wanted to try Ubuntu -- I dl the windows installer one and ran it. As it started it went to the Ubuntu logo and then my screen became half full of different colored horizontal lines, so I rebooted and went into the adv boot and ran the install under safe graphics mode. Now when I boot I get options to boot into 2.6.32-25 and also a recovery and also 2.6.32.24 and a recovery. I left the 2.6.32-25 highlighted and it booted but gave me a msg that said:
(EE) VESA: Kernal modesetting driver in use, refusing to load.
(EE) No devices detected.
Then it goes to a screen that allows me to boot in a low graphics mode. It loads and I dl some security updates with the Update Manager.
What do I need to do in order to boot w/o any faults and also what is the difference from 2.6.32-25 and 2.6.32-24? Which should I be using?
 
Do I need to modify my graphis somehow?
My graphics card is a NVIDIA GeForce 6150 LE
The installed drivers are:
nvd3dumx

---

### Post by atonal on 2010-11-23
anyone????

---

### Post by drs305 on 2010-11-23
Once you boot into Ubuntu, try going to System, Administration, Additional Drivers and see if there is a listing for Nvidia. If so, install that driver.

Normally you should use the latest kernel (25). If it doesn't work but 24 does, then of course use the earlier one.

---

### Post by atonal on 2010-11-24
> **drs305 said:**
> Once you boot into Ubuntu, try going to System, Administration, Additional Drivers and see if there is a listing for Nvidia. If so, install that driver.

Normally you should use the latest driver (25). If it doesn't work but 24 does, then of course use the earlier one.

Worked like a charm -- thanks so much :D

---

