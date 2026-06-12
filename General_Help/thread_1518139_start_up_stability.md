---
title: "start up stability"
date: 2010-06-26
forum: General Help
---

### Post by poppyd on 2010-06-26
I have a AcerTravelmate 4670 and have upgraded to Ubuntu 10 from Ubuntu 9   prior to the upgrade the startup was perfect  now the screen appears to be rotating and though you can just read the sign in when it starts if you select ststem- preferences- monitors and change the resolution from 1024x 768 to 800x600 it immediately stabilers and works fine even if you return to 1024x768 i have downloaded all updates to no avail the acer hax a ATI Mobility Radeon  X1400 card ....   any suggestions??

---

### Post by sukigenseki on 2010-06-26
That is pretty trippy. I my Dell laptop has the same video card in it, and I have had strange issues using the kernel versions supplied by Lucid like plymouth failing to start and other freaky graphical anomalies. Using this kernel from the Ubuntu kernel mainline webpage

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/")

Installing the newer kernel version .debs is totally your call, but it stopped me from having to deal with every 5 or so boots requiring me to force a reset because the system froze at plymouth.

All of my mysterious graphic issues stopped, but for you the first thing I would check is the logs for Xorg after you use the resolution that makes your display rotate to see if they say anything. Or you could just post the log here lol. It should be 

/var/log/Xorg.0.log

that you are looking for, and like I said try to make your screen reproduce the error before you submit the log file.

---

