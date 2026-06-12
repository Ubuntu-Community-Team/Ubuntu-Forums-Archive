---
title: "system crontab works, but root crontab does not"
date: 2010-07-06
forum: General Help
---

### Post by boblu on 2010-07-06
I am having a strange problem here.
If I add the following line to system crontab(/etc/crontab), it works well

> */1 *   * * *   root    /bin/date >> /root/text

but if I use root crontab,

# crontab -e
and add  
> */1 *   * * *   /bin/date >> /root/text

it does not work at all.

Can you please help me on this?
Thank you

---

