---
title: "GRUB start up problem!"
date: 2012-06-10
forum: General Help
---

### Post by ajpearson on 2012-06-10
Sometimes (perhaps 50%) Grub does not kick in when turning my laptop on. All I see is a cursor flashing top left of screen. I have to turn the laptop off (hard key), leave it 10 seconds or so, and then turn back on. Then it normally works but not always.

Any ideas?

Thanks

---

### Post by phran on 2012-06-10
> **ajpearson said:**
> Sometimes (perhaps 50%) Grub does not kick in when turning my laptop on. All I see is a cursor flashing top left of screen. I have to turn the laptop off (hard key), leave it 10 seconds or so, and then turn back on. Then it normally works but not always.

Any ideas?

Thanks
remove the battery and try to operate the laptop with ac as the sole power source.  if the problem goes away, you need a new battery.  let us know what happens.

phran

---

### Post by phran on 2012-06-10
another suggestion: if you have an Ubuntu live cd, try to boot from that.  let us know...

phran

---

### Post by drs305 on 2012-06-10
There are times when a flashing cursor means there is no bootloader information available to the system and installing Grub via a LiveCD will help. 

However, if Grub works 50% of the time this shouldn't be an issue. The problem is more likely a hardware issue in which the BIOS isn't finding the initial MBR/boot sector information for some reason, even though it's there and can be found occasionally. Normally if the system found this information you would get some sort of GRUB prompt rather than a blinking cursor.

---

### Post by ajpearson on 2012-06-10
Thanks for the quick replies. Funny enough Phran, the battery has not worked for a while, so it sounds like that is what is causing the issue.

---

### Post by phran on 2012-06-10
did you try testing whether the laptop could consistently boot into grub without the battery installed?  if it works, then you should consider buying a new battery.

---

### Post by ajpearson on 2012-06-10
Thanks - I will try that.

---

