---
title: "sendmail stopped sending mails (553 5.1.8 reject)"
date: 2010-03-04
forum: General Help
---

### Post by gshockoman on 2010-03-04
I'm developing on my ubuntu 9.10 machine for the web (php).  
I'm using it sendmail for sending mails, and while developing on my local machine, I send local mails (to my user 'doron').  

Up until a few days ago, I was able to send mails both from php's mail() function, and from the command line using the mail command.  
I'm using sendmail with mailutils.  

Since the last few days, it seems like it stopped working.  
When I try to send mail from the command line, I get the following in my syslog (and mail.info, and mail.log):

```
    Mar  3 13:27:58 doron-desktop sendmail[4693]: o23BRwlA004693: from=doron, size=84, class=0, nrcpts=1, msgid=<201003031127.o23BRwlA004693@doron-desktop.>, relay=doron@localhost
    Mar  3 13:27:58 doron-desktop sm-mta[4694]: o23BRwtQ004694: ruleset=check_rcpt, arg1=<doron@doron-desktop>, relay=localhost [127.0.0.1], reject=553 5.1.8 <doron@doron-desktop>... Domain of sender address doron@doron-desktop does not exist
    Mar  3 13:27:58 doron-desktop sendmail[4693]: o23BRwlA004693: to=<doron@doron-desktop>, ctladdr=doron (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30084, relay=[127.0.0.1] [127.0.0.1], dsn=5.1.8, stat=User unknown
    Mar  3 13:27:58 doron-desktop sm-mta[4694]: o23BRwtQ004694: from=<doron@doron-desktop>, size=84, class=0, nrcpts=0, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]

```
Trying to telnet locally to port 25 results in the following (same output for doron@doron-desktop):

```
    doron@doron-desktop:/var/mail$ telnet localhost 25
    Trying ::1...
    Trying 127.0.0.1...
    Connected to localhost.
    Escape character is '^]'.
    220 doron-desktop. ESMTP Sendmail 8.14.3/8.14.3/Debian-9ubuntu1; Wed, 3 Mar 2010 13:26:06 +0200; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
    helo localhost
    250 doron-desktop. Hello localhost [127.0.0.1], pleased to meet you
    mail from: doron@localhost
    250 2.1.0 doron@localhost... Sender ok
    rcpt to: root@localhost
    553 5.1.8 root@localhost... Domain of sender address doron@doron-desktop does not exist

```
However - if I do the same, but use doron@127.0.0.1 in the mail from field, I get:

```
    250 2.1.5 root... Recipient ok
```

My /etc/hosts file:

```
    127.0.0.1       localhost
    127.0.1.1       doron-desktop doron-desktop.

```
(If I don't have the "doron-desktop." (with the ending dot), the mail command takes a lot of time (around 30 seconds) until it responds, but the results are the same.)


Anyone have an idea of why and how can I fix this ?
Thanks,
Doron

---

### Post by rahmtech on 2010-09-13
I am having he exact same issue.  I have been searching google for days without any luck.  If anyone has any advice, it would be greatly appreciated.
 
Thanks in Advance,
Chris

---

