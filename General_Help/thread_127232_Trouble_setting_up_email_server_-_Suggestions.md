---
title: "Trouble setting up email server - Suggestions?"
date: 2006-02-08
forum: General Help
---

### Post by jagipson on 2006-02-08
Hello world!

I am trying to setup an email server on a headless (i.e. no keyboard/montor) system which does *not* have XServer installed.  I have been using 'aptitude' to install and uninstall packages.  I know that I have installed and uninstalled Postfix, exim, and Courier MTA's, Maildrop and Procmail MDAs, and Dovcot and Courier imap/pop servers, but not all of these at the same time.  Currently I have Postfix and Dovecot.  I'm having some trouble, probably because I wasn't sure how to 'cleanup' between switching email server types (besides purging the packages).  

[COLOR="Red"]Before[/COLOR] I get too deep into fixing these, I want to review whether these are the best choices for my needs.

[COLOR="Blue"]I Need:[/COLOR]
per mailbox support for filters (spamassassin, clamav)
Maildir-style mail stores
IMAP over SSL

[COLOR="Blue"]I Want:[/COLOR]
maildir quotas, if possible
mailboxes tied to real user accounts (no virtualization)

What do you suppose the best set of tools would be, given these requirements?

--Jeff

---

