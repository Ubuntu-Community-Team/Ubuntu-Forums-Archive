---
title: "evolution refuses to retrieve mail only from one source"
date: 2012-03-11
forum: General Help
---

### Post by rebeltaz on 2012-03-11
I am running Evolution 2.28.3 (Ubuntu 10.04) and it has just this weekend begun to refuse to retrieve email from my AT&T/Bellsouth account. It gives me this error:

Failed to read a valid greeting from POP server pop.att.yahoo.com

Evolution has no trouble pulling email from my 1&1 email accounts, though.

My girlfriend is able to get mail from the same (AT&T) server using the same POP settings, but she is running Thunderbird.

Any ideas, other than run Thunderbird? :)

---

### Post by dcstar on 2012-03-12
> **rebeltaz said:**
> I am running Evolution 2.28.3 (Ubuntu 10.04) and it has just this weekend begun to refuse to retrieve email from my AT&T/Bellsouth account. It gives me this error:

Failed to read a valid greeting from POP server pop.att.yahoo.com

Evolution has no trouble pulling email from my 1&1 email accounts, though.

My girlfriend is able to get mail from the same (AT&T) server using the same POP settings, but she is running Thunderbird.

Any ideas, other than run Thunderbird? :)
Run this command and see if you get a response:
```
telnet pop.att.yahoo.com 110
```
You should get something like this:
```
Trying 67.195.135.148...
Connected to pop-sbc.mail.am0.yahoodns.net.
Escape character is '^]'.
+OK hello from popgate 2.48.1 on pop123.sbc.mail.sp2.yahoo.com
```
If you don't get it, then you have a networking issue.

---

### Post by rebeltaz on 2012-03-12
Hi.. yes. I do get the correct response.

---

### Post by robarm38 on 2012-03-12
> **dcstar said:**
> Run this command and see if you get a response:
```
telnet pop.att.yahoo.com 110
```
You should get something like this:
```
Trying 67.195.135.148...
Connected to pop-sbc.mail.am0.yahoodns.net.
Escape character is '^]'.
+OK hello from popgate 2.48.1 on pop123.sbc.mail.sp2.yahoo.com
```
If you don't get it, then you have a networking issue.
I'm having the same problem since installing latest kernel update (2.6.32-39), excpet I'm using Yahoo Mail. I run the telnet command and get a response saying "unable to connect to remote host, connection timed out." I installed Thunderbird and it works fine. Should I just quit using Evolution and transfer all my folders, addresses and archives over to Thunderbird?

---

### Post by rebeltaz on 2012-03-12
I, too, installed Thunderbird just to make sure and it does work, so this appears to be a bug in the update.

My problem with going to Thunderbird is that I have six email accounts and Thunderbird wants to create an Inbox for each account whereas Evolution places all incoming mail in one common Inbox.

---

### Post by dcstar on 2012-03-14
> **rebeltaz said:**
> Hi.. yes. I do get the correct response.

Then check the settings for the problem account to make sure that things like SSL/TLS are set or unset where they are supposed to be the other.

If you were using Encryption then the update may have changed things, so try turning it off.

---

### Post by rebeltaz on 2012-03-15
Nah, all of the settings are right. After this last update, everything is working right again. Like I said, must have been a bug in the update.

---

