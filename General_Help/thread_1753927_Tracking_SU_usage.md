---
title: "Tracking SU usage?"
date: 2011-05-09
forum: General Help
---

### Post by c911darkwolf on 2011-05-09
is there a terminal command where i can see how many times a user attempted to use SU ?  like how many times they were successfull and unsuccessfull?

---

### Post by bodhi.zazen on 2011-05-09
It is logged in /var/log/auth.log

You can grep / awk yourself into some kind of a report.

grep uer_name /var/log/auth.log

will get you started, from there depends on what you want the output to look like. you can add uniq, wc, etc.

If you want a more complicated report, look at awk or perl.

If you need help please be more specific on what help you want with what step, what kind of information you want, etc.

---

