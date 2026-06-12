---
title: "execute a java program without ssh connection"
date: 2011-05-09
forum: General Help
---

### Post by cucucur on 2011-05-09
hello! I would like that my java program continues executing when I close the ssh connection, how can I do that?

I suppose I have to create a service, but I have no idea how to do it!


Thanks!!!

---

### Post by ziekfiguur on 2011-05-09
You might want to try using screen, see `man screen' for more info.

---

### Post by cucucur on 2011-05-09
perfect!! thank you so much!!

---

### Post by sj1410 on 2011-05-09
you can also use cron to schedule the start of the program.

---

