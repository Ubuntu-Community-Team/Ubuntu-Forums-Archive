---
title: "GEdit process won't automatically stop when window is closed"
date: 2011-01-24
forum: General Help
---

### Post by Menyus on 2011-01-24
I recently upgraded to Ubuntu version 10.10 64-bit and since then closing GEdit won't stop the process automatically when the window is closed and I have to kill it manually. I didn't have this problem with version 10.04 (also 64-bit) and I didn't change any settings after the upgrade. Any ideas?

Thanks.

---

### Post by earthmeLon on 2011-01-24
Is the window staying open (maybe turning grey), or is the window closing but you're checking 'ps -e | grep gedit' to see if the process is still open?

You could try opening up a terminal and then running gedit within it.  The terminal must stay open while gedit is open, and it will show you lots of information and errors.  Try closing gedit and seeing what the terminal outputs when you do so.

---

### Post by Menyus on 2011-01-24
No, the window closes normally. I only noticed the problem because, on reboot, the message would pop up that GEdit is still running, etc. I get the PDI with top and kill the GEdit process manually. I do not seem to have this problem with any other application.

p.s. I do have the GMate plugin installed but I had that under v10.04 already w/o any problems.

---

