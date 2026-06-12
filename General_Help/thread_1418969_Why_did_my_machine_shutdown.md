---
title: "Why did my machine shutdown?"
date: 2010-03-01
forum: General Help
---

### Post by poldie on 2010-03-01
Where would I start looking to investigate why my PC shut down by itself last night?

It's Ubuntu 9.10 64bit, on a PC I built myself (q6600 quad core cpu, 4 gigs of ram).  

Are there any logfiles which might contain a last minute panic message of some sort?  The machine is very stable and I'm not aware of this happening before. I don't believe I have a problem with overheating or powersupply (the PSU is way overspecced for the load).

---

### Post by zeroseven0183 on 2010-03-01
Yes, try to check **Log File Viewer **in System > Administration.

---

### Post by poldie on 2010-03-01
> **zeroseven0183 said:**
> Yes, try to check **Log File Viewer **in System > Administration.

Thanks - I'll try that out later today.  I did look manually through the files in /var/log (or logs) which had changed since the reboot and didn't spot anything, but then again, i'm not sure exactly what i'm looking for.

---

### Post by zeroseven0183 on 2010-03-01
Is your computer plugged to a UPS? Were there any power fluctuation in your area that time?

---

### Post by 10101011 on 2010-03-01
Are you sure there were no power-blips?

That's usually the cause in my case (my UPS has a dead battery).

---

### Post by poldie on 2010-03-01
> **10101011 said:**
> Are you sure there were no power-blips?

That's usually the cause in my case (my UPS has a dead battery).

I'm not aware of any, but how would I know?  It's possible. 

It happened around 4am this morning. I did use the computer then, and I would have quit the browser and then gone back to bed, and I heard it powering down just as I got into bed.  There's no way I could have accidentally powered down when I quit the browser.  No-one else was using anything else at that time of the morning!

If it was a blip, then I guess there'd be nothing in the logs.  Apart from power loss, are there other times when there'd be likely to be nothing in the log?  Which log would you look in to see how/when/why Ubuntu was shut down?

---

