---
title: "ubuntu lucid LTS unresponsive when left unattended"
date: 2010-06-10
forum: General Help
---

### Post by blackandwhitepandabear on 2010-06-10
Hi, I recently upgraded from 8.04 (Hardy) to 10.04 (Lucid). I usually leave my Linux box running as an SSH server (setting on never sleep) while traveling so I can access files, and so on, but since upgrading, I am no longer able to connect via SSH, and upon my return the fan suggests the computer is still running (not sleeping), but the screen is dark and keyboard/mouse cues will not "wake it up". Any thoughts? Thanks!

---

### Post by Woody1987 on 2010-06-10
Do you run compiz? Since upgrading i have the same problem and i diagnosed it as compiz. Disable it and it may fix your problem.

---

### Post by wkulecz on 2010-06-10
Another possibility is, I have a system that runs 6.06 and 8.04 fine, but to boot 10.04 I needed to add the acpi=oldboot to the kernel boot options, otherwise it locked up during the install or boot sequence.

Three other (newer) motherboards and one older, I've installed 10.04 didn't need this so I've ended up wasting most of today figuring it out :(

---

### Post by Metrop021 on 2010-06-10
ah, i have this problem, my guess is that your computer is going into sleep mode. Mine was doing the same and it looked like as if it was on (still humming), the sleep mode in ubuntu seems to be extremely buggy, and most hits on google confirm that. Go to the power manager (somewhere in the administration menu), and set the timer for sleep to 'never'.

---

### Post by blackandwhitepandabear on 2010-06-10
Thanks - I do have the energy settings to Sleep: Never already, and it does boot okay. Just stops working after I leave it for a while. I turned off the Compiz (if it was ever on?) with Alt+F2 and metacity --replace &. So guess I just have to wait a few days to see if it stops again...

---

