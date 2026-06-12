---
title: "Move old email from Outlook Express into Dovecot"
date: 2009-08-09
forum: General Help
---

### Post by cliveb on 2009-08-09
I'm in the process of replacing the household Windows server with an Ubuntu machine. (The client machines will remain Windows). I'm currently looking into moving the email facility.

I would like to use an IMAP server to hold all the emails centrally - this will allow people to view their email from any machine in the house that happens to be running (rather than having to boot up their own PC as happens now because everything is POP3 based). Or have I misunderstood that?

I've found the necessary documentation to set up a Dovecot IMAP server, and as far as I can tell it will be possible to configure the various Outlook Express clients to use IMAP instead of POP3.

I'm left with the issue of how to transfer lots of old emails stored in local Outlook Express accounts onto the Dovecot server. The messages can be copied out as .eml files, which appear to be RFC822 conformant text files. Is it possible to import those .eml files into Dovecot? (The Dovecot wiki has sections about importing from other IMAP or POP3 servers, but I couldn't find anything about importing raw mail files). If so, can anyone point me at some documentation that explains how to do it?

Thanks.

---

### Post by ellgor on 2009-08-09
Hi,

Check out "Kmail" it can import directly from Outlook and a host of othersn (pop3 and or imap).

Regards, Ellgor.

---

