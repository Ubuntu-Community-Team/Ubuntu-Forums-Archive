---
title: "Postfix wont deliver mail"
date: 2011-04-06
forum: General Help
---

### Post by martinlall on 2011-04-06
Hi,

My postfix stopped working suddenly. It worked months before.

If I do test:
```
mail -s "testmail" mymailaddr@gmail.com < /dev/null
```

I see in logs:
```
Apr  6 09:10:30 Pegasus postfix/pickup[11350]: 26319320AAE: uid=0 from=<root>
Apr  6 09:10:30 Pegasus postfix/cleanup[11503]: 26319320AAE: message-id=<20110406061030.26319320AAE@Pegasus.localhost>
Apr  6 09:10:30 Pegasus postfix/qmgr[11351]: 26319320AAE: from=<root@Pegasus.localhost>, size=3296, nrcpt=1 (queue active)
Apr  6 09:10:31 Pegasus postfix/smtp[11505]: 26319320AAE: to=<mymailaddr@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.229.27]:25, delay$
Apr  6 09:10:31 Pegasus postfix/qmgr[11351]: 26319320AAE: removed
```

By the logs, it should of gotten through. But it never did. None of my mails wont reach it's destination anymore.
Can anyone help me with that?

---

### Post by martinlall on 2011-04-06
Figured it out. My IP address were blocked by some agency.

---

