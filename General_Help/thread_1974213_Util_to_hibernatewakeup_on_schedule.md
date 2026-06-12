---
title: "Util to hibernate/wakeup on schedule"
date: 2012-05-05
forum: General Help
---

### Post by serverpimp on 2012-05-05
I have a Ubuntu box in a detached garage (not air conditioned) that I rsync important files from my house.  Poor man's DR site.  :)   Now that it's getting warmer I would like to find a way to hibernate and wake up the Ubuntu box at scheduled times during the day to take the rsync job from my Mac in the house.  I looked at qshutdown that seems to work well to take the box to the hibernate/suspend mode but it doesn't seem to have a way to wake it up (no wake from LAN either).

Is there something in the OS that can do this?  If not, what other tools are out there that may solve this issue?

Recap:  wake up at 3:50PM every day.   Hibernate at 6:00PM.   Wake on LAN (ssh into the Ubuntu box) would be perfect.

Thanks

---

### Post by dcstar on 2012-05-05
> **serverpimp said:**
> I have a Ubuntu box in a detached garage (not air conditioned) that I rsync important files from my house.  Poor man's DR site.  :)   Now that it's getting warmer I would like to find a way to hibernate and wake up the Ubuntu box at scheduled times during the day to take the rsync job from my Mac in the house.  I looked at qshutdown that seems to work well to take the box to the hibernate/suspend mode but it doesn't seem to have a way to wake it up (no wake from LAN either).

Is there something in the OS that can do this?  If not, what other tools are out there that may solve this issue?

Recap:  wake up at 3:50PM every day.   Hibernate at 6:00PM.   Wake on LAN (ssh into the Ubuntu box) would be perfect.

Thanks

You can usually set up a BIOS "Wake up" and then use whatever OS that boots to shut down.

---

