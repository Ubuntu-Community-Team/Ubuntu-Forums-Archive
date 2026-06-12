---
title: "grep help"
date: 2010-12-10
forum: General Help
---

### Post by nsnidanko on 2010-12-10
Hi,
 
Can someone help me with regex in grep? I need to match ANYTHING in the following with any character combination (something like * in findstr in C):
 
grep "Delivery of nonspam" /var/log/mail.log | grep "to [EMAIL="ANYTHING@harperdd.com"]ANYTHING@harperdd.com[/EMAIL]"
 
Thank you

---

### Post by Paddy Landau on 2010-12-17
You can use wildcards in grep using regexp. Use *man grep* to check the precise syntax for grep and Google regexp.

In your case, you need to say you want "any character", which a dot represents, "any number of times", which an asterisk represents. Hence:

```
grep 'Delivery of nonspam' /var/log/mail.log | grep 'to .*@harperdd.com'
```You can get more specific, such as disallowing spaces in the email address, but I'll leave that to you.

---

