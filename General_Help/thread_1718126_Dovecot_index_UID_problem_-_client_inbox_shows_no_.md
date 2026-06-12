---
title: "Dovecot index UID problem - client inbox shows no messages!"
date: 2011-03-30
forum: General Help
---

### Post by tomasch on 2011-03-30
OK folks - I'm lost here.
I have postfix/dovecot running on Ubuntu Server 10.04 - been fine for a long time - but...

Dovecot is 1.2.9

I played around on one user ~/Maildir directory and then the imap mail client no longer "sees" the emails - the inbox is empty. It tells me there are 47 emails in total and 17 unread - which is correct because I can see them using Webmin.
I can also see the emails in the /cur directory but they do not show up on the client inbox.

I have deleted the user's dovecot* files so that the index and UID are rebuilt but the inbox on the client still is empty.

I've tried RoundCube, an iPad and and Thunderbird client - same result - empty inbox.

All other user emails are fine (mostly because I have not screwed them up too) so the configuration is working fine - and again it was working for months prior to me mucking about in there

Any ideas what to do or why the imap clients show an empty inbox

TIA

Tom

---

