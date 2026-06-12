---
title: "Mail codepage from command line"
date: 2010-11-11
forum: General Help
---

### Post by Wtower on 2010-11-11
Hi,

I use the following line in a cron script in my ubuntu server.

```
echo "Blah blah" | mail -s "Blah" mail@address.com
```

Where blah blah is info in other locale. The mail sent is by default in utf-8 but I would need it in some other codepage as iso8859-7. I wonder if there is some way I can change the mail encoding.

---

