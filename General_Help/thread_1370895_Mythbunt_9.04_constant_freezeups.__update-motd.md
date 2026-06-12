---
title: "Mythbunt 9.04 constant freezeups.  update-motd?"
date: 2010-01-02
forum: General Help
---

### Post by pombe on 2010-01-02
My mythbox is constantly freezing up so I checked to if there was anything in the "syslog" and found that the same line occurs prior to the restart sequence after I reset the machine.

```
Dec 31 18:40:01 mythbox /USR/SBIN/CRON[18634]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

Anyone know what this is?

Edit: ok, its "Message of the Day"...  trying to get rid of chron-job...

---

### Post by pombe on 2010-01-03
Ok.  I deactivated update-motd (I think) and the random freezes are still occurring. The last logged action of each session is now something else.

What are the steps for troubleshooting general lockups?

I figure I will start with: 
1) clean out all the dust bunnies from the case   
2) Run memtest to check the ram.

---

