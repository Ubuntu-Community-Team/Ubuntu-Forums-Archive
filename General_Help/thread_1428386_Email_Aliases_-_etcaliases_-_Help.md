---
title: "Email Aliases - /etc/aliases - Help"
date: 2010-03-12
forum: General Help
---

### Post by M1GEO on 2010-03-12
I am trying to create a setup where email to my domain is checked for the specific aliases in the /etc/aliases file.  If it does not match, then to send it to the admin account.

To clarify, as I am aware that isn't too clear:  If mail arrives for [email]admin@domain.tld[/email] then it sent to the admin user (this is simple).  The same for webmaster for example.  However, I would like to be able to create a random email address at my TLD, and have it redirect to my account, so for example, if an email is sent to [email]random@domain.tld[/email], and "random" doesnt have an entry in the aliases file, the mail is lost.  How can I overcome this?  I was initially thinking of wildcards in the /etc/aliases file, but it appears this isn't possible (Googled a few pages).

Cheers All...

---

