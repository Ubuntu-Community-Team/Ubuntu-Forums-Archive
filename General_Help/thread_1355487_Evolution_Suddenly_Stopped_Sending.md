---
title: "Evolution Suddenly Stopped Sending"
date: 2009-12-15
forum: General Help
---

### Post by Dagonus on 2009-12-15
Ubuntu 9.10
Evolution 2.28.1
Mail.com account. 

Up to today, I was using:

Server: "smtp1.mail.com"

X : Server Requires Authentication

Use Secure Connection : :No Encryption"

Authentication:
Type: "Login" 
Username: "name:mydomain.com#mail.com"

Up until today that worked fine. Now, nothing happens. Evolution receives mail and then sits at 1 of X on the sending, not sending anything nor giving any error. 


Mail.com currently reads:
 * The outgoing mail (SMTP) server address is: smtp.mail.com, port: 587.
* Your user name is your MAIL.com email address.
 * Your password is your MAIL.com password. 

so I changed Server to "smtp.mail.com:587"

No change. 

So I changed username to "name@mydomain.com" 

No change. Set server back to original with changed username, nothing. 

Did something get changed in a recent update over the weekend and I just got it today resulting in a problem somewhere or should I get on mail.com's tail and find out if they've got an alternate login server(I "think" smtp1.mail.com already was one from a problem I had long ago, so I don't know why both would suddenly stop working)

Anyone else have mail.com and know what's up?

Edit: 

Oh, and if it helps at all, if I "Check for Supported Types" for authentication for smtp, evolution says it's checking, but nothing comes of it. In POP3 settings, it reports immediately.

---

### Post by dcstar on 2009-12-15
> **Dagonus said:**
> Ubuntu 9.10
Evolution 2.28.1
Mail.com account. 

Up to today, I was using:

Server: "smtp1.mail.com"

X : Server Requires Authentication

Use Secure Connection : :No Encryption"

Authentication:
Type: "Login" 
Username: "name:mydomain.com#mail.com"

Up until today that worked fine. Now, nothing happens. Evolution receives mail and then sits at 1 of X on the sending, not sending anything nor giving any error. 


Mail.com currently reads:
 * The outgoing mail (SMTP) server address is: smtp.mail.com, port: 587.
* Your user name is your MAIL.com email address.
 * Your password is your MAIL.com password. 

so I changed Server to "smtp.mail.com:587"

No change. 

So I changed username to "name@mydomain.com" 

No change. Set server back to original with changed username, nothing. 

Did something get changed in a recent update over the weekend and I just got it today resulting in a problem somewhere or should I get on mail.com's tail and find out if they've got an alternate login server(I "think" smtp1.mail.com already was one from a problem I had long ago, so I don't know why both would suddenly stop working)

Anyone else have mail.com and know what's up?

Edit: 

Oh, and if it helps at all, if I "Check for Supported Types" for authentication for smtp, evolution says it's checking, but nothing comes of it. In POP3 settings, it reports immediately.

```
telnet smtp.mail.com 587
```

That address no longer works, I believe you are supposed to use your local ISP SMTP server or your Ubuntu MTA.

---

### Post by Dagonus on 2009-12-15
[quote=Mail.com Customer Service]We are aware that a subset of our user base is experiencing services issues with POP / SMTP services. We are working to resolve this issue as quickly as possible and will provide an update on status via email as soon as additional information is available. We apologize for any inconvenience this may have caused.[/quote]

Well I guess that explains it. Their end. not mine.

---

