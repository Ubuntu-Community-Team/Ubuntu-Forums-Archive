---
title: "Postfix 2.8.6 won't collect mail off server"
date: 2011-11-08
forum: General Help
---

### Post by brosskgm on 2011-11-08
I went back to sendmail. It's working for now. Thanks.

---

### Post by dcstar on 2011-11-09
> **brosskgm said:**
> I installed postfix 2.8.6 to replace sendmail since I've run postfix for many years.

Problem I'm having, I can receive email from the internet and it's placed in the Maildir as wanted.

I can telnet localhost 25 or IP address just fine and even send.

The problem is when I use a remote machine with outlook or thunderbird it goes through the motions of checking the email but says no new messages when there is messages sitting in the Maildir/new directory
........

Postfix is **not** a server for mail clients, it is a MTA for communicating with other MTAs and receiving mail to be sent to MTAs. Install an IMAP or POP server if you want mail clients to pick up mail off a server.

---

### Post by brosskgm on 2011-11-09
I understand that. I'll leave it at mbox for a while until I get it figured out.

> **dcstar said:**
> Postfix is **not** a server for mail clients, it is a MTA for communicating with other MTAs and receiving mail to be sent to MTAs. Install an IMAP or POP server if you want mail clients to pick up mail off a server.

---

