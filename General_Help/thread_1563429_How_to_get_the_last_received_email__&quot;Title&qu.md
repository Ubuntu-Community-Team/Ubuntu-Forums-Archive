---
title: "How to get the last received email  &quot;Title&quot; field only?"
date: 2010-08-29
forum: General Help
---

### Post by honeybear on 2010-08-29
Hi

I have configured fetchmail to let me know with fetchmail -ks 
when I receive a message. I would like to output the title only of the last send email
fetchmail -k | head -n 1 says how much email have been sent, but would be great to display the last mail and keep it on imap server if possible

```
poll "imap.gmail.com" proto imap port 993
    user "me@gmail.com" password "XXXXXX"
    ssl


```

---

