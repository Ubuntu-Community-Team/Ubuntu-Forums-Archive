---
title: "Headphone jack stopped working after update to 8.1"
date: 2010-03-26
forum: General Help
---

### Post by -spy on 2010-03-26
It worked fine with 8.04, although it wasn't as loud as it usually is with windows, but since I've updated its stopped working. When plugging the headphones in, a little sound comes through for a second when halfway plugged in, then nothing when fully plugged.

Any idea on how to fix this?

---

### Post by -spy on 2010-03-28
bump

---

### Post by lidex on 2010-12-25
Depends. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

