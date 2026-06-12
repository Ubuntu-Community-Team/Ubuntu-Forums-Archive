---
title: "conky /var/mail/&lt;user&gt; update new_mails count"
date: 2010-02-25
forum: General Help
---

### Post by rippin on 2010-02-25
I've scoured the Web and the manpage trying to figure how to have localhost email update new_mails count but am clearly missing something since, after reading and deleting mail from mbox, the mail count remains the same. Here's the code

> 
mail_spool /var/mail/cmo

  and

mbox $alignr${new_mails [-i 60]} new messages
What am I missing?
Many thanks,

---

