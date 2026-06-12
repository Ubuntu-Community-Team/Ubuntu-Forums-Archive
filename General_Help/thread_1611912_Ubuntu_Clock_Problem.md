---
title: "Ubuntu Clock Problem"
date: 2010-11-02
forum: General Help
---

### Post by libertov on 2010-11-02
Ok I have been using Ubuntu since 9.04 and everything has been great. I dual boot my machine with Windows 7 (for work) I have a Dell M90 laptop. I upgraded from 10.04 to 10.10 last night and I noticed a funny thing with my clock. It is set back an hour, and everything i do will not fix it, after i reboot it goes back an hour.

I have windows 7 set to NO synchronizing with websites and I also set Ubuntu to NO UTC. But it keeps changing my clock in the bios also.

Anyone have any help the can assist me with?

---

### Post by Barajqial on 2010-11-02
Yeah, I've been having this same problem with a dell dimension 3550 set to dual boot xp home and 10.04.  Also on another xp machine at my work and there is no Ubuntu on that one all other 150 comps or so don't have this issue, I've been at a loss.  Problem cropped up 2 days ago.

---

### Post by LuxVoodoo on 2010-12-22
I just did a fresh install of Unbuntu 10.10  on a new Windows 7 64 bit rig.  I have it set up to dual boot between the two OSes and noticed this very problem with the clock, only that it resets my clock about five hours behind each time I boot into the Ubuntu partition.  If I stick to the Windows 7 partition, the clock doesn't change.  But if I boot into Ubuntu first, then then Windows, the clock moves back by five hours.  I've been dual booting Ubuntu for years and this has never been an issue before.  Strange.

---

### Post by mcduck on 2010-12-22
> **LuxVoodoo said:**
> I just did a fresh install of Unbuntu 10.10  on a new Windows 7 64 bit rig.  I have it set up to dual boot between the two OSes and noticed this very problem with the clock, only that it resets my clock about five hours behind each time I boot into the Ubuntu partition.  If I stick to the Windows 7 partition, the clock doesn't change.  I've been dual booting Ubuntu for years and this has never been an issue before.  Strange.

..and let me guess, you live in UTC-5 timezone? ;)

Linux- and Unix systems by default assume that the computer's clock runs in UTC, and then calculate the time to display to user from their current time zone.

On the other hand Windows assumes that the system clock runs in your local time.

Check */etc/default/rcS* and make sure it has following line included:
```
UTC=no
```

---

### Post by Dave_L on 2010-12-22
An alternate solution (configuring Windows to use UTC) is discussed here:

[http://ubuntuforums.org/showthread.php?t=1591792](http://ubuntuforums.org/showthread.php?t=1591792)

---

