---
title: "Current Updates hang installing.  Ubuntu 11.10"
date: 2012-03-10
forum: General Help
---

### Post by byte69 on 2012-03-10
I have having an issue where I show 17 updates they download and are applying then seems to just hang.  It never finishes and I have left it in this update mode for 12 hours.  It never finishes.   

Any ideas???

I have also done apt-get clear and apt-get update.  Same problem.

---

### Post by raja.genupula on 2012-03-10
from where you're trying to do that , i mean terminal or update manager ? 

this problem i have faced in my starting days of Ubuntu . its look like a BUG . you can report it .

---

### Post by byte69 on 2012-03-11
> **raja.genupula said:**
> from where you're trying to do that , i mean terminal or update manager ? 

this problem i have faced in my starting days of Ubuntu . its look like a BUG . you can report it .
I have tried both ways at CLI and with the GUI.  It does not matter.  It gets stuck both ways.   I tried clearing and tried the updates again.  Same issue.

---

### Post by byte69 on 2012-03-11
Found the issue.   I ran it apt-get upgrade it downloaded fine again.  But then it appears to open a change log which opens vi.   It is at : so I did q and once that closed vi it continued the install of all updates.   The change log is for ffmpeg for Chrome.

---

