---
title: "Best strategy to schedule rsnapshot if pc is not always on?"
date: 2010-06-20
forum: General Help
---

### Post by MichaëlVD on 2010-06-20
I just did my first rsnapshot backup of my /home/ to an external harddisk. When I am not at my computer for a couple of hours, I always shut it down. Therefore, there are no predictable hours of the day where I know that my computer is running. So, how should I schedule/crontab my rotating rsnapshot backups?

Is anyone using rsnapshot in combination with a schedule which is not based on exact times but rather on the time the computer is running?

---

### Post by Goodseeker on 2010-06-20
You may want to consider a software package called "anacron", which is in the official Ubuntu repository and is supported by Canonical.

---

### Post by MichaëlVD on 2010-06-20
Thanks! Anacron is indeed just what I needed.

---

