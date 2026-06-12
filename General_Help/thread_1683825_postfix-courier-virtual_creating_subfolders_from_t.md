---
title: "postfix-courier-virtual: creating subfolders from the terminal"
date: 2011-02-08
forum: General Help
---

### Post by cipe53 on 2011-02-08
I have installed courier/postfix/ubuntu with virtual domains as per Flurdy and all is working. 

From an IMAP client, users are able to create folders and move messages to them. These changes I can see reflected under /var/spool/mail/virtual/<user.name>.

I would like to migrate folders and messages from the old courier/exim/ubuntu mail server to the new. When I create folders in /var/spool/mail/virtual/<user.name> via maildirmake.courier, these folders are not recognised by the IMAP client (we have tried two clients). Google suggested I use maildiracl, which makes sense, but I cannot even get the -list command to work. I do not think I understand the arguments for maildiracl -list maildir folder.


I have not been able to Google an answer.

Any suggestions

---

