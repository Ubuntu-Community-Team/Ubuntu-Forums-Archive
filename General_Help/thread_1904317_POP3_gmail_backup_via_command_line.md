---
title: "POP3 gmail backup via command line"
date: 2012-01-04
forum: General Help
---

### Post by alphaamanitin on 2012-01-04
Is is possible to use the linux command line to easily access my gmail account via POP3 and download all my emails as text?  Specifically, could I set up a script to run, either automatically every X days, or manually?

Thanks,

AlphaA

---

### Post by Buntumatic on 2012-01-04
Fetchmail can do the fetching part, what you do after is up to you. You could run an IMAP server for instance to read your mail.
[http://www.axllent.org/docs/networking/gmail_pop3_with_fetchmail](http://www.axllent.org/docs/networking/gmail_pop3_with_fetchmail)

---

### Post by alphaamanitin on 2012-01-04
Looks good but in my quick look (at work cannot spend too much time messing around) does it download a copy or the original, does it keep username and password in plaintext?  Need to look into this more, sounds like exactly what I want.

AlphaA

---

