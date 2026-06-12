---
title: "crontab not working"
date: 2009-07-17
forum: General Help
---

### Post by xiaomahe on 2009-07-17
My crontab seems not able to do the task that i want it to do..

i did from an example for a website..

what i did is:

1. sudo crontab -e
2. * * * * * wall test

save the configuration, and it says ok

but i wait after a minute, there is nothing comeout,

---

### Post by t4thfavor on 2009-07-17
Try 

1-59 * * * * /path/to/wall whatever

wall only reads stdin

so like cat file.txt |wall

---

