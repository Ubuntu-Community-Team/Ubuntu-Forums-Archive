---
title: "SATA hard drive, cable, amd MB bus"
date: 2012-09-10
forum: General Help
---

### Post by azmyth on 2012-09-10
I've been struggling today with a hard drive that would go into read only mode as I was getting errors in the dmesg related to sata. The system was doing an update and it crashed on me and I was unable to do anything since it said I needed to run dpkg --reconfigure -a but the computer would freeze on me during the command. For the heck of it, I swapped out the sata cable and I changed the sata bus on the MB where the drive was plugged into. I rebooted and now I was able to run --reconfig. I then was able to install smartools and I ran a short test and it said no errors. Guess my question is I can't believe the cable and/or bus location switch would fix the problem. Is this too good to be true? I thought the HD was going bad.

---

