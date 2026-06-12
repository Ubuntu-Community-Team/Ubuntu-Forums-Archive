---
title: "shutdown -h now"
date: 2010-10-09
forum: General Help
---

### Post by sr_guy on 2010-10-09
I am planning to write a simple script to use cron to shutdown my PC at a certain time. So I was wondering if shutdown -h now is the equivalent to the halt command, and if I do use shutdown -h now, will WOL work? I have WOL working when I do a simple halt.

---

### Post by Gunman1982 on 2010-10-09
> **sr_guy said:**
> I am planning to write a simple script to use cron to shutdown my PC at a certain time. So I was wondering if shutdown -h now is the equivalent to the halt command, and if I do use shutdown -h now, will WOL work? I have WOL working when I do a simple halt.

After having a short glimps at the man pages of halt and shutdown I would suggest you use shutdown over halt. And yeah it will shut your computer down and yes your Wake-On-Lan should work.

---

