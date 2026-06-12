---
title: "Why SMTP Server?"
date: 2010-10-28
forum: General Help
---

### Post by karthick87 on 2010-10-28
I am using [COLOR=Red]POSTFIX[/COLOR](smtp server) as my [COLOR=Red]MTA[/COLOR]..But i can only send mails by [COLOR=Red]SMTP RELAY USING GMAIL[/COLOR].So what is the use of having post fix..?Why should we have an intermediate to forward our message from one smtp server to another smtp server..?Pls correct me if i am wrong

---

### Post by HermanAB on 2010-10-28
That is how email works.  It travels by SMTP over port 25.  

Your ISP is blocking port 25 outgoing.  If you pay them a few dollars extra a month then they will give you a static IP address and allow you to use port 25.

---

### Post by karthick87 on 2010-10-28
No my isp is not blocking port 25..I have scanned it with nmap and the port 25 is open.

---

### Post by karthick87 on 2010-10-28
```
karthick@Ubuntu-desktop:~$ telnet smtp.gmail.com  25
Trying 74.125.53.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP w22sm14958569wfd.19

```

So my port is open right..?

---

