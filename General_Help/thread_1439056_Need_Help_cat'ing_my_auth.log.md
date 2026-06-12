---
title: "Need Help cat'ing my auth.log"
date: 2010-03-25
forum: General Help
---

### Post by Loves SSH on 2010-03-25
Hi folks,

I'm looking for a command to pipe into that removes cron jobs from my auth.log for easier readability when using cat. Any suggestions? 

TIA!

---

### Post by patchwork on 2010-03-25
```
cat /var/log/auth.log | grep -iv cron
```

---

### Post by Loves SSH on 2010-03-25
Beautiful! Thanks patchwork!

---

