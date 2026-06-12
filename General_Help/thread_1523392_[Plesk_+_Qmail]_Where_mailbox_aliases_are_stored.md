---
title: "[Plesk + Qmail] Where mailbox aliases are stored?"
date: 2010-07-03
forum: General Help
---

### Post by prodigy_ on 2010-07-03
There's a bit tricky and unusual question but maybe someone knows the answer.

I have a mail server with Plesk Panel 9.2 and Qmail. Plesk allows to create mail accounts via GUI and I know that these accounts are stored in **/var/qmail/mailnames/<domain.name>** directory. Plesk also allows to create aliases. Let's say, I have a mailbox **example@example.com**. I can add an alias (e.g. **example2@example.com**) associated with the same mailbox. These aliases work, no problem here.

Obviously these aliases have to be stored somewhere too. I know that system-wide ones are in **/var/qmail/alias** directory.

But I need account-specific ones. Does anyone know where to find them? I looked in all obvious locations but no luck so far...

---

