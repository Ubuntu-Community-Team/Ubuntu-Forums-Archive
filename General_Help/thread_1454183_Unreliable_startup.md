---
title: "Unreliable startup"
date: 2010-04-14
forum: General Help
---

### Post by AVHATION on 2010-04-14
I am running 9.04 Jaunty with an AMD processor and NV11 (GeForce2 MX/MX400) AGP card. I shut down the machine every night. The machine has become increasingly difficult to start up from cold during recent months; the screen freezes sometimes during the boot cycle, or during Ubuntu loading, or a few minutes after loading Ubuntu and using Forefox or Evolution. Sometimes the reboot cycle starts automatically. (An unresolved symptom which may or may not be relevant is that when the mouse button is clicked the results are that 2 clicks have happened - I work around this by rapidly clicking for about 10 secs.)  The POST produces a "one beep" normally, unless the screen has frozen beforehand. No hardware has been changed. Recent software changes, apart from routine Ubuntu updates, are a script blocker and Evolution/Firefox auto back ups. Memtest 86 and hard drive tests are OK.  The CMOS battery is the original (c.5 years old). Once the machine has run for a few minutes it will run all day, so cooling must be OK.

After the screen freezes sometimes, sometimes with disc access light on, I can restart using the warm or cold buttons, other times I have to switch off at the wall to get the number lock to extinguish. The following messages have sometimes been displayed:
crc error - system halted
The greeter application appears to be crashing
1-065-9281 Kernel panic 0 not syncing; attempted to kill init
Not starting K Display Manager; it is not default display manager

All ideas welcome!

Henry

---

### Post by AVHATION on 2010-05-02
Upgrading to 10.4 seems to have improved matters. So far, no problems with starting up, although occasionally the mouse 2 clicks for 1 symptom still occurs. I have also replaced the CMOS battery and the power supply which may or may not be relevant. The upgrade provided me the opportunity to use the Nvidia graphics driver appropriate to my AGP card which may or may not be relevant. Hope this does not confuse other novices.

---

### Post by itiswhatitis on 2010-05-02
You can adjust your mouse settings under System->Preferences->Mouse
It  may be that your settings are a little off.  I've attached a screenshot of my settings.  

I'm curious, why did you replace your power supply?  If you had a surge or burnt up the old one, it's possible that your motherboard might have been damaged.

CRC error could be RAM or Hard Drive...

**Hard Drive:**
System->Administration->Disk Utility
Select your drive, then click on **Check File System**
If you have a drive that is SMART capable, you may have an option to run those tests as well.

**Memory:**
You should have an option on your boot menu for MemTest86+.  You can use this to see if you are having any memory issues.

---

### Post by AVHATION on 2010-08-20
I ended up replacing the machine with a second hand one. Starting and mouse quirks are no longer a problem but I have now run into crashing issues which are the subject of a new thread. The only hardware that is common is the data hard drive.

---

