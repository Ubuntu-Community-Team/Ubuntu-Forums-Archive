---
title: "not booting after update"
date: 2010-09-06
forum: General Help
---

### Post by Uncas on 2010-09-06
Hi,
I was in the middle of an update on my acer mini one netbook with 10.04 netbook remix and had to leave.  I closed my lid hoping to continue de update home.  When I try to boot up, the machine gets to the login screen and it seems that it freezes there.  I tried rebooting and going in to safe mode and it seems that it freezes also.  I got a liveUSB and decided to try that and it works, but my data on one of my partitions is old, theres nothing of the new files I had earlier.  Is there any way for me to troubleshoot the boot to see whats bothering my girl?

Thanks,

Uncas.

---

### Post by Uncas on 2010-09-07
While booting in safe mode the computer halts with the following message...
 
[drm:edid_is_valid] *ERROR* EDID has major version 0, instead of 1
[drm:edid_is_valid] *ERROR* raw EDID:
 
i915 0000:00:02.0: LVDS-1: EDID invalid.
 
Please advice...

---

### Post by Uncas on 2010-09-07
When I boot normal everything looks nice but when I get to the login nothing works.  The mouse doesn't move, I can''t get the keyboard working, Alt+Ctrl+Del doesn't work, Alt+Ctrl+F8 doesn't work.  I have to power it down via the power button.
 
Any ideas!?!?
 
Anyone
 
Anyone
 
Buller
 
Buller
 
Ferris Buller

---

### Post by Uncas on 2010-09-08
Bump

---

### Post by JohnHeikkila on 2010-09-08
When you boot, try to go to the GRUB menu.
You can access it by holding SHIFT when you see the white thing flashing on a black screen (GRUB 2.0) or by pressing Esc when it says you can press Esc (GRUB Legacy). Then select the Recovery mode, and try to get to the root console mode. If you get to the console mode, run "dpkg --configure -a" or "dpkg-reconfigure -a"

---

### Post by Uncas on 2010-09-08
Thanks JohnHeikkila for your answer.  When I boot in the recovery console I get what you see in message #2.  I can't get to the prompt.

---

### Post by Uncas on 2010-09-09
Please refer to the following link for the documentation of what I did.
 
[http://ubuntuforums.org/showthread.php?t=1570075](http://ubuntuforums.org/showthread.php?t=1570075)
 
Uncas.

---

