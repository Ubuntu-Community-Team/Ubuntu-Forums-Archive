---
title: "printf in bash history"
date: 2010-03-25
forum: General Help
---

### Post by GavinSpearhead on 2010-03-25
My cd commands in bash seem to get replaced by `printf "%b"`s e.g.

cd /media/downdisk/urd3/tmp
becomes
cd "`printf "%b" '\0057media\0057downdisk\0057urd3\0057tmp'`"

And it only happens to cd commands, none other as far as I can see. 
(e.g. tail -f /var/log/apache2/access.log is just fine)

Any ideas how to prevent / fix this?

---

### Post by prodigy_ on 2010-03-25
Do you use mc by any chance? Anyway, since "0057" is octal for ASCII slash character, commands in your log are perfectly valid. :-)

---

### Post by GavinSpearhead on 2010-03-29
Yes I do use mc occasionally. But it happens to _all_ cds but no other commands. 

And I know they are valid.  It's just tedious reading and editing them.

---

