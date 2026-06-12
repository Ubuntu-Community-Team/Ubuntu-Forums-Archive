---
title: "Email program and forward issue"
date: 2012-02-23
forum: General Help
---

### Post by goboni on 2012-02-23
DEAR All,
I am using UBUNTU version 11.10
The system (cron) sends me emails to [EMAIL="root@domain.com"]root@domain.com[/EMAIL]
Other programs send me emails also to other emails out of my server.
 
1. How can I know via which email program (mail server program) these emaisl are sent (sendmail / potfix / exim)?
 
2. I configure in multiple places my willing to forward root emails to another address [EMAIL="x@y.com"]x@y.com[/EMAIL] . 
I tried adding /root/.forward file with the address and modified /etc/aliases. 
None of these methods help. 
Any suggestions?
 
THANKS

---

### Post by dcstar on 2012-02-23
> **goboni said:**
> 
.........
I tried adding /root/.forward file with the address and modified /etc/aliases. 


And did you update the aliases database after you modified the file?

---

### Post by goboni on 2012-02-23
YEs, by newaliases command

---

### Post by Khayyam on 2012-02-23
> **goboni said:**
> [...] 1. How can I know via which email program (mail server program) these emaisl are sent (sendmail / potfix / exim)?

If you look at the mail headers you will see "Received: by host.domain.tld" followed by the MTA (Mail Transfer Agent), "Postfix", "Sendmail", "qmail", etc. 
 
> **goboni said:**
> 2. I configure in multiple places my willing to forward root emails to another address. I tried adding /root/.forward file with the address and modified /etc/aliases. None of these methods help. Any suggestions?

Not all mailservers support .forward by default, some (like qmail) have to be configured to do so. Postfix does, but I'm not sure about Exim.

Your .forward contains nothing else but the address, right?

HTH ... khay

---

### Post by goboni on 2012-02-24
Thanks!
 
> **Khayyam said:**
> If you look at the mail headers you will see "Received: by host.domain.tld" followed by the MTA (Mail Transfer Agent), "Postfix", "Sendmail", "qmail", etc. 
 
I found it and it is "Exim 4.76"
 
> **Khayyam said:**
>  
Your .forward contains nothing else but the address, right?

 
Right, and it still do **not** work.
Any suggestions?

---

### Post by goboni on 2012-02-24
I was able to fix it from here and would like to share.
 
For Exim you need to edit the rewriting e-mail addresses file: /etc/exim4/email-addresses 
I just added one line:
```
 
echo "root@LocalHost: X@Y.Z" >> /etc/exim4/email-addresses

``` 
 
Then I just test it using:
```
 
echo "This is a test." | mail -s Testing1 root

``` 
More can be find here: [http://wiki.debian.org/GmailAndExim4](http://wiki.debian.org/GmailAndExim4) 
 
Thanks for the help!

---

### Post by goboni on 2012-02-27
the test worked for me but the cron still sends mail to the wrong address of root and not rewrite it...
Please help

---

