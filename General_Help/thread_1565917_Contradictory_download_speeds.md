---
title: "Contradictory download speeds"
date: 2010-09-01
forum: General Help
---

### Post by t0p on 2010-09-01
I'm currently downloading some files using **wget**.  According to wget, the download speed is 40-45K/s.  But according to the System Monitor, I'm downloading at a rate of 80-100KiB/s.

What can explain this contradiction in download speeds?  I'm not downloading updates or anything like that: wget, so far as I can tell, is the only downloading.

---

### Post by garyedwardjohnston on 2010-09-01
assuming that no other app on your desktop is using the internet it might be the units.  kilobits per second vs. kilobytes per second.  there are 8 bits in a byte so you may have to do math :(

---

### Post by t0p on 2010-09-03
> **garyedwardjohnston said:**
> assuming that no other app on your desktop is using the internet it might be the units.  kilobits per second vs. kilobytes per second.  there are 8 bits in a byte so you may have to do math :(

But 40 kilobits per sec = 320 kilobytes.  That, by itself, does not explain the discrepancy.

---

