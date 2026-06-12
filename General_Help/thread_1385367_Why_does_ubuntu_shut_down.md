---
title: "Why does ubuntu shut down?"
date: 2010-01-19
forum: General Help
---

### Post by AWilco on 2010-01-19
I have a copy of desktop ubuntu running on a computer that acts as a server (I like the desktop). However when it is left alone it will after a number of hours shut down by itself, and I can't work out why. The Power Management settings say 'Never'. I've tried looking in the log viewer for info on what causes it, but I can't find any information. Does anyone know where else I can investigate?

Thanks.

---

### Post by plucky on 2010-01-19
> **AWilco said:**
> I have a copy of desktop ubuntu running on a computer that acts as a server (I like the desktop). However when it is left alone it will after a number of hours shut down by itself, and I can't work out why. The Power Management settings say 'Never'. I've tried looking in the log viewer for info on what causes it, but I can't find any information. Does anyone know where else I can investigate?

Thanks.

Does it go to sleep and wakes up when you move the mouse or type on the keyboard or do you have to press the power button to re-start it?

Check the power saving settings in the BIOS.

Good Luck

---

### Post by john newbuntu on 2010-01-20
One category of problems include overheating of CPU, fans not working properly, heatsink problems, vents gathering dust etc.

---

### Post by AWilco on 2010-02-24
To bring this point back up again. Ubuntu shuts down after exactly 5 hours of uptime, every time. This rules out overheating or self-protection issues. my BIOS has no options for a shutdown timer or anything (although there is some issues in that it says it should, but opening the menu gives no option for it). So presumably its something in Ubuntu? Any more ideas?

Oh, and it completely shuts down and powers off the computer, its not a suspend or hibernate state or anything.

---

### Post by dabl on 2010-02-24
After it does it's auto-shutdown thing, I would boot a Live CD and take a look at the /var/log/syslog file on the installed system -- maybe it will give a clue as to what happened.

---

### Post by b0b138 on 2010-02-24
Check crontab for an entry to shutdown

---

### Post by doas777 on 2010-02-24
> **AWilco said:**
> To bring this point back up again. Ubuntu shuts down after exactly 5 hours of uptime, every time. This rules out overheating or self-protection issues. my BIOS has no options for a shutdown timer or anything (although there is some issues in that it says it should, but opening the menu gives no option for it). So presumably its something in Ubuntu? Any more ideas?

Oh, and it completely shuts down and powers off the computer, its not a suspend or hibernate state or anything.


it may be a power/voltage issue, but if the timing is exactly 300 minutes, then it is likely a software issue.

---

### Post by Diptansu on 2010-02-24
Its probably due to overheating of CPU .. me too having this problem for some days irrespective of windows or ubuntu. Recently I made some rearrangements thus CPU do not remain at a conjested place and it can radiate the heat and cool down .. the problem is almost over now .

---

### Post by Mansteel on 2010-02-24
I have the same problem. I do not have any control of temperature or voltage in my bios. 
But how can this be fixed?

Seems like my problem has something to do with heat because when i take my laptop to bed then it shuts down faster than if i have it on a table. that could maybe be sign of bad ventilation?

---

### Post by doas777 on 2010-02-24
> **Mansteel said:**
> I have the same problem. I do not have any control of temperature or voltage in my bios. 
But how can this be fixed?

Seems like my problem has something to do with heat because when i take my laptop to bed then it shuts down faster than if i have it on a table. that could maybe be sign of bad ventilation?

yes. never use a laptop on anything but a hard flat surface, and make sure your little rubber "feet" are still there. also consider getting the local laptop person to blow it out for you. 
I use a cooling plate with my laptop, that dropped my avg core temp by about 20 deg C. my turion idles at about 35C instead of the previous 55-65.

is not likely related to the ops issue, since they clam it comes up at a regular interval.

---

### Post by lavinog on 2010-02-24
> **AWilco said:**
> To bring this point back up again. Ubuntu shuts down after exactly 5 hours of uptime, every time. This rules out overheating or self-protection issues. my BIOS has no options for a shutdown timer or anything (although there is some issues in that it says it should, but opening the menu gives no option for it). So presumably its something in Ubuntu? Any more ideas?

Oh, and it completely shuts down and powers off the computer, its not a suspend or hibernate state or anything.

If you have the time, you could try booting into a recovery console and see if still shuts down.  That should eliminate hardware/bios causes.
what version of ubuntu is this?

Does it do a proper shutdown? Do you get any fsck errors on the startup.
Did it always do this or only recently?

---

### Post by AWilco on 2010-02-26
Couldn't find any other entries in crontab. I'm running Ubuntu 9.10, how do I boot into recovery console?

syslog doesn't give any hint as to what causes the shutdown, just shutdown messages suddenly appear. It might be VDR, which I've installed but not really configured, I've killed that to see what happens.

---

### Post by doas777 on 2010-02-26
> **AWilco said:**
> Couldn't find any other entries in crontab. I'm running Ubuntu 9.10, how do I boot into recovery console?

syslog doesn't give any hint as to what causes the shutdown, just shutdown messages suddenly appear. It might be VDR, which I've installed but not really configured, I've killed that to see what happens.

have you confirmed that it happens at an exact interval, based on the log info?

---

