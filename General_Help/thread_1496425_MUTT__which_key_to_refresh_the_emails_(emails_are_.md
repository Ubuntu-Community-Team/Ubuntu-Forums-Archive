---
title: "MUTT : which key to refresh the emails (emails are got by IMAP)?"
date: 2010-05-29
forum: General Help
---

### Post by frenchn00b on 2010-05-29
How to refresh and reload the list of email into MUTT ? Which key?

additional:
   how to go to folder SENT of gmail ? and configureation eventually?
Best regards

---

### Post by germanix on 2010-05-29
[http://www.mutt.org/doc/manual/](http://www.mutt.org/doc/manual/)

everything you need you will find in this manuel

---

### Post by nazwa on 2012-02-15
Maybe someone will find this information useful

If you want to refresh your IMAP mailbox you can put following line into your .muttrc file:

```

bind index "^" imap-fetch-mail
```

and refresh your mailbox by pressing ^ . Of course you can use your own assignment.

If you want to change folder to Sent in gmail you have to press default letter c and navigate to Sent. "[Gmail]/Sent" to be more precise.

---

### Post by oldos2er on 2012-02-15
Closed, necromancy.

---

