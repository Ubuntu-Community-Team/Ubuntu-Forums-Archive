---
title: "Bind 9 connection problem.Help Please"
date: 2012-02-07
forum: General Help
---

### Post by tejli007 on 2012-02-07
Hi all.
after 3 days and nights of trying i dident make my own nameserver.So please i will need your help.
 
I have installed bind 9.
i have make the configurations like in howtoforge.com
when i dig mydomain.com i got the answer:
 global options: +cmd
;; connection timed out; no servers could be reached
 
someon got idea how to fix it?
 
thanks

---

### Post by jonobr on 2012-02-07
Hi

Silly question but is bind running?

Can you share your configurations with us?

If you 

```
sudo /etc/init.d/bind9 restart
```
what errors if any do you see?

---

