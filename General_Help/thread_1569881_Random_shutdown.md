---
title: "Random shutdown"
date: 2010-09-07
forum: General Help
---

### Post by Sapper41 on 2010-09-07
Hi very cherry here to ubuntu, and i've run into a problems. Ubuntu will randomly pop up the shutdown menu and then shutdown. It seems to happen when im in firefox and typing and it has been difficult to replicate. I dont think it is a temp issue since watch sensors shows temmp of 40-50C. Someimtes it happens every minute someimtes i can go 10min without it happening, any ideas?

Dell Inspiron 1525
ubuntu 10.04 (only os on system)

---

### Post by Sapper41 on 2010-09-07
No one?

---

### Post by gldearman on 2010-09-07
Are you monitoring the GPU's temperature (i.e., the temperature of the video card's processor), or just the CPU temperature?  If it is a temperature issue, your video card is as likely a culprit as your CPU.  Have you tried running with visual effects disabled, to see if that may be the problem?

Failing that, try poking around in the files in /var/log/.  Wait until the next random shutdown, then wait several minutes, reboot, and go check which of those log files changed at or since the time of the shutdown.  Then, go through those, looking for error messages at around the time of the shutdown.  Once you have error messages, you have something to google or to post here.

That's all I can offer you.  Hope it helps.

---

### Post by Sapper41 on 2010-09-07
ty I will do that, that is the CPU temp monitor and this laptop has the integrated graphics, no actual card I think, I with search the sensors again to make sure i turned them all on. Running a memtest for the last 6 hours and it all checked out fine. I will look into the /var/log next.

---

