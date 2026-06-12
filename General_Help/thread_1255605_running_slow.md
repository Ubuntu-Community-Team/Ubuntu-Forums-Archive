---
title: "running slow"
date: 2009-09-01
forum: General Help
---

### Post by shane8002 on 2009-09-01
hey guys fresh install of jaunty is running extremly slow. Took 3 hours to install updates which normally takes 10 minutes on my laptop. The install is on a dell desktop pentium 4 1.8 GHZ, 512mb of ram any ideas???  it wont even run 2 programs smoothly it almost like slow motion.

---

### Post by Tamlynmac on 2009-09-01
If I may ask a few questions?

What video are you using and is it sharing any of your onboard ram? What % of cpu and ram are you using "system/administration/system monitor/resources tab"?

While in the "system monitor" you can check the "Processes" tab to identify any processes that may be running and using excessive resources.

I suspect this may be a hardware problem (video) - are you running Compiz or visual effects? If so turn them off and watch for an improvement in speed. Your system may not be capable of running Visual Effects with 9.04 (without a memory upgrade) especially if your video is sharing any of your onboard ram and/or has limited, if any ram of it's own.

Just some thoughts - hope they help.

---

### Post by paradigm2 on 2009-09-01
Tamlynmac gives good advice.  Also if you can try to upgrade the memory to at least 1 GB.  It makes a big difference overall and it is likely your bottleneck.  Back to Tamlynmac's advice, check in particular Firefox.  Sometimes it can be a processor hog on my P4.

---

### Post by shane8002 on 2009-09-01
Im not running visual effects at all, i killed some processes yesterday like bluetooth and stuff im not using, didnt help. The cpu is about 20 percent just using firefox, memory 40 percent, and swap 14 percent. The thing is this computer had windows xp on it and it ran fine and used to play halo on it and it handled fine with the graphics turned down, thats what dosent make sense and i know linux runs "lighter" than windows so thats why i dont understand it, if it was slow in windows I wouldnt expect it to do this but it wasnt....

---

### Post by NoaHall on 2009-09-01
Add the cpu scaler applet to the panel, and increase it to the maximum that your cpu can take. see if anything has improved.

---

