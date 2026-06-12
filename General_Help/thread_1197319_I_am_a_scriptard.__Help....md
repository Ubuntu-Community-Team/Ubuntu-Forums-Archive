---
title: "I am a scriptard.  Help..."
date: 2009-06-26
forum: General Help
---

### Post by Hawk__0 on 2009-06-26
I cannot figure out what is wrong with my if statements after doing this all bloody day at work with no issues.

Somebody please tell me why this:

if [ $now = "Y" ] then
date >> file.txt
fi

gives me this:

line 22: syntax error near unexpected token `fi'

---

### Post by ad_267 on 2009-06-26
I think the first line is missing a semi-colon:
if [ $now = "Y" ]; then

---

### Post by kpkeerthi on 2009-06-26
```

if [ $now = "Y" ]; then
     date >> file.txt
fi

```

---

