---
title: "Damaged hard drive &amp; interrupted update"
date: 2010-04-10
forum: General Help
---

### Post by Slothful on 2010-04-10
A section of the hard drive on my laptop is damaged but the laptop has genearlly been running fine as it seems to very rarely touch that section (once every few months). However, when installing some updates the computer has hit that section which means it becomes unresponsive and makes a nasty clunking sound every 10s or so. Because of this I've had to abort the update but now whenever I try to run 'dpkg --configure -a' to sort out the problem caused by the interrupted update I get the same freezing up and clunking. The message that appears when I run the command is 
adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...
and then it freezes.

Does anyone have any ideas how I can get resolve this?

Thanks
David

---

### Post by dcstar on 2010-04-10
> **Slothful said:**
> A section of the hard drive on my laptop is damaged but the laptop has genearlly been running fine as it seems to very rarely touch that section (once every few months). However, when installing some updates the computer has hit that section which means it becomes unresponsive and makes a nasty clunking sound every 10s or so. Because of this I've had to abort the update but now whenever I try to run 'dpkg --configure -a' to sort out the problem caused by the interrupted update I get the same freezing up and clunking. The message that appears when I run the command is 
adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...
and then it freezes.

Does anyone have any ideas how I can get resolve this?


Boot off the latest 10.04 beta Live CD and use the Disk Utility to do a SMART test on your hard drive.

That will (hopefully) move the data from the faulty blocks on you drive, or at least mark them as bad.

---

### Post by Slothful on 2010-04-16
Thanks dcstar, I didn't have the 10.04 live cd so I tried one of the earlier ones instead and was able to fix the problem with e2fsck.

---

