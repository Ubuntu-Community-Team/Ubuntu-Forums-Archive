---
title: "SSMTP Authorization Failed"
date: 2011-02-20
forum: General Help
---

### Post by tankmil on 2011-02-20
Can someone please tell me what I am doing wrong?

This is my ssmtp.conf file:

```

root=[my address]@gmail.com
mailhub=smtp.gmail.com:587
AuthUser=[my address]@gmail.com
AuthPass=[password]
UseSTARTTLS=yes

```And this is what I do on the command line, and what I get in response:

```

:~$ ssmtp [recipient address]
To: Some guy
From: Another guy
Subject: testing

essmtp: Authorization failed (535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 l12sm3234587qcu.31)

```

---

### Post by n8bounds on 2011-07-03
I'm having the same problem....

My /etc/ssmtp/ssmtp.conf
```

# The user that gets all the mails (UID < 1000, usually the admin)
root=me@gmail.com

# The mail server (where the mail is sent to), both port 465 or 587 should be acceptable
# See also http://mail.google.com/support/bin/answer.py?answer=78799
mailhub=smtp.gmail.com:587

# The address where the mail appears to come from for user authentification.
rewriteDomain=

# The full hostname
hostname=localhost

# Use SSL/TLS before starting negotiation
#UseTLS=Yes
UseSTARTTLS=Yes

# Username/Password
AuthUser=me@gmail.com
AuthPass=MYSTRONGPASSWORD
AuthMethod=LOGIN

# Email 'From header's can override the default domain?
FromLineOverride=yes

```

And get this:
```

ssmtp -v me@gmail.com < testemail 
[<-] 220 mx.google.com ESMTP g16sm4128400qcs.11
[->] EHLO localhost
[<-] 250 ENHANCEDSTATUSCODES
[->] STARTTLS
[<-] 220 2.0.0 Ready to start TLS
[->] EHLO localhost
[<-] 250 ENHANCEDSTATUSCODES
[->] AUTH LOGIN
[<-] 334 VXNlcm5hbWU6
[->] bjhib3VuZHNAZ21haWwuY29t
[<-] 334 UGFzc3dvcmQ6
[<-] 535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 g16sm4128400qcs.11
ssmtp: Authorization failed (535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 g16sm4128400qcs.11)


```

---

### Post by n8bounds on 2011-07-03
I figured it out.

I had a "#" in my password. Change your password to something simple then test.

---

### Post by stacktracer on 2011-09-06
10,000 points for n8bounds. Thanks!

---

### Post by j1nn on 2012-08-21
For all those without any special chars, but still having Authorization failed (535): Google is simply blocking your "new" IP. Login via the web interface to the account you are trying to use, check the logins and tell google it's you.
(took me several to days to figure it out, thanks for the informative message, google..)

---

### Post by n8bounds on 2012-08-21
> **j1nn said:**
> For all those without any special chars, but still having Authorization failed (535): Google is simply blocking your "new" IP. Login via the web interface to the account you are trying to use, check the logins and tell google it's you.
(took me several to days to figure it out, thanks for the informative message, google..)

Cool, thanks.

---

