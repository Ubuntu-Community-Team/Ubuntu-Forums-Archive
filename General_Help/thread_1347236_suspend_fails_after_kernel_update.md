---
title: "suspend fails after kernel update"
date: 2009-12-06
forum: General Help
---

### Post by TVAbuntu on 2009-12-06
After today's kernel update to 2.6.31-16, my suspend stopped working automatically from gnome-power-manager. It will work from the taskbar and gdm, but requires the control key to be pressed to bring up an unlock screen (which I don't have set in g-p-m). Intel core duo chip with video chipset of 82G33/G31 Express. 
It has worked perfectly since 8.04 until today.
Looking at Xorg log (and understanding I really have no idea what I'm doing) I see that DPMS stanby/suspend is "off" (log attached). Is this the problem?

---

### Post by TVAbuntu on 2009-12-06
Actually I don't think it was the kernel update, as when I run the prior kernel the same thing happens. I see xorg was updated as well. A likely culprit?

---

### Post by TVAbuntu on 2009-12-06
Seems to be working again this morning, without any intervention.
????

---

### Post by bowwave on 2009-12-09
I had the same problem. I found out that if I unmount all of my nautilus sshfs mounts before suspending, things work fine again. I don't know if this also applies to SMB and other mounts.

---

