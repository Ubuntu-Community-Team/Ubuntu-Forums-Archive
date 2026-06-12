---
title: "smtp issues in evolution with smtp.mail.me.com at iCloud"
date: 2012-05-28
forum: General Help
---

### Post by geoffatmk on 2012-05-28
I have Ubuntu 12.04 and am running evolution 3.2.3.

Virgin email have decided to close non subscriber accounts so I am trying to set up my [email]xxxx@me.com[/email] account in evolution to be my new default account.

I have searched the web for information and tried all that I can but still cannot get smtp to work.  I have connected to the imap server to retrieve emails but I cannot get a connection to the smtp server.

I have tried SSL but it will not connect to the server to tell me what type of authentication to use.

When I use TLS on port 587 as recommended, it connnects to the server for the authentication type (plain or login) but no matter which I use, it does not allow me to send.

Is anyone else using me.com on their evolution?  If so can anyone point me to a soluton?

---

### Post by dcstar on 2012-05-29
> **geoffatmk said:**
> I have Ubuntu 12.04 and am running evolution 3.2.3.

Virgin email have decided to close non subscriber accounts so I am trying to set up my [email]xxxx@me.com[/email] account in evolution to be my new default account.

I have searched the web for information and tried all that I can but still cannot get smtp to work.  I have connected to the imap server to retrieve emails but I cannot get a connection to the smtp server.

I have tried SSL but it will not connect to the server to tell me what type of authentication to use.

When I use TLS on port 587 as recommended, it connnects to the server for the authentication type (plain or login) but no matter which I use, it does not allow me to send.

Is anyone else using me.com on their evolution?  If so can anyone point me to a soluton?

[https://secure.dslreports.com/forum/r22295282-Re-Ubuntu-NoobChanging-SMTP-port-in-Evolution-Mail](https://secure.dslreports.com/forum/r22295282-Re-Ubuntu-NoobChanging-SMTP-port-in-Evolution-Mail)

---

### Post by geoffatmk on 2012-05-30
Thanks David that was veryh helpful.  Finally got it working using TSL after a reboot.

Geoff

---

