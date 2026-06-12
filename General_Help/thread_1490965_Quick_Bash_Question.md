---
title: "Quick Bash Question"
date: 2010-05-23
forum: General Help
---

### Post by nirvana21 on 2010-05-23
This is a quick question I can't seem to solve but it can't be too hard.

I need single quotations around everything right of the equal sign, but it obviously won't work because of the other single quotes. I tried double quotations, parenthesis, and a few other things to no avail.

```
alias abnormal=awk '{ if ($6 != "MARK" && $5 != "--" && $7 != "--") print $0 }' /var/log/messages
```

How do I resolve this? Thanks!

---

### Post by arevirlegna on 2010-05-23
> **nirvana21 said:**
> This is a quick question I can't seem to solve but it can't be too hard.


Nirvana21,
Try this:

```
alias abnormal="awk '{ if (\$6 != \"MARK\" && \$5 != \"--\" && \$7 != \"--\") print \$0 }' /var/log/messages"
```Here, I am using " at the outer-most level, but I then need to protect the inner ones by escaping them with a \ ... Notice that the $ symbol of the positional variables needs to be escaped too. Give it a go.

Cheers!

---

### Post by nirvana21 on 2010-05-23
Thanks, works perfect.

---

