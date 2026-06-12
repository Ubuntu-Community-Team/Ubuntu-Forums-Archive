---
title: "Rsyslog and eat CPU; /var/log eats HDD"
date: 2009-11-11
forum: General Help
---

### Post by LucidStrike on 2009-11-11
Logging seems a bit too intensive or buggy in my Karmic setup. Didn't notice until I was informed that I had about 200MB left on the partition. It read 0KB within minutes. Searched around for large files and emptied the trash, but none of it added up to what was missing. I had read about out of control /var/log files, so I checked there and deleted all of the contents, after verifying that it was taking up the vast majority of the space. I think that initially freed about 40GB, but over 100GB had been freed after a reboot. Yeah, a couple of applications complained but nothing concerning.

Now, rsyslogd and dd eat 35% and up from boot, with no applications running. My CPU is workin' really hard for nothing.

---

