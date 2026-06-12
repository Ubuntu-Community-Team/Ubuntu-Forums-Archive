---
title: "How to cancel Back in Time backup"
date: 2010-02-09
forum: General Help
---

### Post by afrodeity on 2010-02-09
I'm busy running back in time for the first time and stupidly including the /media folder. The application is now backing up my backup drive and the drive is running out of space. How do I cancel the backup? I've tried quitting but it just starts right up again.

---

### Post by SlugSlug on 2010-02-09
ps -ef will show all running processes 
ps -ef |grep -i time  may show back in time -- note the number in first coloum (pid)

sudo kill (pid)

---

