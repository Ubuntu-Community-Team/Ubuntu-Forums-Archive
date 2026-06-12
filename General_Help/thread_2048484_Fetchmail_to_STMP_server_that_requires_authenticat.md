---
title: "Fetchmail to STMP server that requires authentication"
date: 2012-08-26
forum: General Help
---

### Post by beuges on 2012-08-26
I need to have fetchmail deliver to an Exchange server that requires SMTP client authentication. Fetchmail connects to the server, but it does not authenticate itself. As a result, the delivered mail is rejected. Does fetchmail support authenticating the SMTP connection, and if so, what options do I need to set? 
 
fetchmailrc:
```
#set daemon 30
set logfile /var/log/fetchmail.log
#set syslog
#set no rewrite
defaults
        proto pop3
        uidl
        nokeep
        fetchlimit 10
        ssl
        smtphost myexchangeserver/587
        sslproto TLS1
poll mypop3server
        esmtpname exchangeserverusername
        esmtppassword exchangeserverpassword
        username "me" there is "exchangeserveremailaddress" here
        password "pop3password"
        no rewrite
;

```
 
Here's what happens:
 
```
fetchmail: 6.3.9-rc2 querying mypop3server (protocol POP3) at Sun 26 Aug 2012 23:12:51 SAST: poll started
<connected to my pop3 server and retrieved some mail>
fetchmail: 2 messages for me at mypop3server (7447 octets).
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 5661
fetchmail: POP3> TOP 1 99999999
fetchmail: POP3< +OK headers follow.
fetchmail: reading message me@mypop3server:1 of 2 (5661 octets)
fetchmail: Trying to connect to ex.ch.an.ge/587...connected.
fetchmail: SMTP< 220 myexchangeserver Microsoft ESMTP MAIL Service ready at Sun, 26 Aug 2012 21:12:51 +0000
fetchmail: SMTP> EHLO myfetchmailserver
fetchmail: SMTP< 250-myexchangeserver Hello [my.ip.ad.dy]
fetchmail: SMTP< 250-SIZE 36700160
fetchmail: SMTP< 250-PIPELINING
fetchmail: SMTP< 250-DSN
fetchmail: SMTP< 250-ENHANCEDSTATUSCODES
fetchmail: SMTP< 250-STARTTLS
fetchmail: SMTP< 250-AUTH
fetchmail: SMTP< 250-8BITMIME
fetchmail: SMTP< 250-BINARYMIME
fetchmail: SMTP< 250 CHUNKING
fetchmail: SMTP> MAIL FROM:someone@somewhere SIZE=5661
fetchmail: SMTP< 530 5.7.1 Client was not authenticated
fetchmail: SMTP error: 530 5.7.1 Client was not authenticated

```
 
The exchange server advertises both starttls and auth, but fetchmail doesn't appear to try to authenticate. Is it possible to get fetchmail to do this without having to set up an MTA to do it?

---

### Post by beuges on 2012-08-27
bump for some post-weekend visibility

---

### Post by andrew.46 on 2012-11-29
I cannot help with this specific problem bu the best people to ask would be the fetchmail-users mailing list:

[http://lists.berlios.de/mailman/listinfo/fetchmail-users](http://lists.berlios.de/mailman/listinfo/fetchmail-users)

Hope this helps?

---

