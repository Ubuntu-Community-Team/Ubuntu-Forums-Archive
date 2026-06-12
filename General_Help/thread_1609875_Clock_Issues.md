---
title: "Clock Issues"
date: 2010-10-30
forum: General Help
---

### Post by wanzeo on 2010-10-30
I recently installed 10.10, and I have not been able to get the gnome panel clock to work correctly. 

I will set it to the correct time, but every time I reboot it will be wrong by several hours. I have never had a problem in previous versions and I have always set the clock by right-clicking on the clock -> Preferences ->Time Settings. 

Am I doing something wrong or is there an easy way to synchronize with a time server? Any suggestions much appreciated.

---

### Post by gmargo on 2010-10-31
Edit the file **/etc/default/rcS** and change the **UTC=yes** entry to **UTC=no**.  Then reboot. The hardware clock is assumed to be in UTC if yes or Local time if no.

---

