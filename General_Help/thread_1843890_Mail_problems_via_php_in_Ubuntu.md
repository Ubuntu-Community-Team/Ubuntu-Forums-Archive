---
title: "Mail problems via php in Ubuntu"
date: 2011-09-14
forum: General Help
---

### Post by renoy29985 on 2011-09-14
Hello,

I have a simple code for sending email in PHP.

I installed postfix (sudo apt-get install postfix).

I compiled the code and it was successful. The mail() function in php  returned value=1. But I am not able to see any mail to the email address  where I sent it.

I changed the myhostname in main.cf file in /etc/fostfix to a meaningful  domain name rather than 'ubuntu' (which was default in the file)

Please help.

Thank you,
Renoy.

---

### Post by kimda on 2011-09-14
Check if postfix is working properly. You can send an email from the commandline to check. ex. mail -s test [email]me@mydomain.com[/email] You can use a gmail account for example to test this. If its not arriving check in /var/log the mail logs like mail.err, mail.log, mail.info etc.

---

### Post by renoy29985 on 2011-09-14
I tried the below (after installing mailutils):

$ mail -s test -t [EMAIL="renoy29985@gmail.com"]renoy29985@gmail.com[/EMAIL]
Cc: [EMAIL="renoy29985@hotmail.com"]renoy29985@hotmail.com[/EMAIL]
 
But it does not return me the prompt :-(
.
.
.
Well it worked after pressing ctl+d. But I still didn't get any mail :-( .. Will check any logs ..

---

### Post by renoy29985 on 2011-09-14
The mail.log file has the below message :

 Sep 14 05:13:42 ubuntu postfix/smtp[3436]: C9709C4F58: to=<renoy29985@gmail.com>, relay=none, delay=723, delays=571/0.1/1    52/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[209.85.225.27]:25: Connection timed out)

says "Connection Timed Out"

---

### Post by kimda on 2011-09-14
Is the postfix server behind a router? Maybe you need to forward port 25 to the machine behind the router. Have a look at this tread:

[http://www.howtoforge.com/forums/showthread.php?t=18781](http://www.howtoforge.com/forums/showthread.php?t=18781)

If its your homemachine you can also try to use relayhost parameter in main.cf to relay the mail to your isp's mailserver. ex. 
relayhost = mail.myisp.com

---

### Post by renoy29985 on 2011-09-19
I tried sending/forwarding (as interpreted by Postfix) a message to myself (renoy29985) in ubuntu and the Mail is sent.

But when I check the log, I see that the mail is DELIVERED before, the Postfix SMTP API is called. Please see the below :

443 Sep 19 08:06:01 ubuntu postfix/pickup[2993]: 53C7AC5093: uid=1000 from=<renoy29985>

444 Sep 19 08:06:01 ubuntu postfix/cleanup[3225]: 53C7AC5093: message-id=<20110919150601.53C7AC5093@ubuntu>

445 Sep 19 08:06:01 ubuntu postfix/qmgr[1099]: 53C7AC5093: from=<renoy29985@sanrays.com>, size=315, nrcpt=1 (queue active)

446 Sep 19 08:06:01 ubuntu postfix/cleanup[3225]: 5EBB7C5092: message-id=<20110919150601.53C7AC5093@ubuntu>

447 Sep 19 08:06:01 ubuntu postfix/qmgr[1099]: 5EBB7C5092: from=<renoy29985@sanrays.com>, size=439, nrcpt=1 (queue active)

448 Sep 19 08:06:01 ubuntu postfix/local[3227]: 53C7AC5093: to=<renoy29985@sanrays.com>, orig_to=<renoy29985>, relay=local, d    elay=0.09, delays=0.07/0.01/0/0.01, dsn=2.0.0, status=sent (forwarded as 5EBB7C5092)

449 Sep 19 08:06:01 ubuntu postfix/qmgr[1099]: 53C7AC5093: removed

450 Sep 19 08:06:32 ubuntu postfix/smtp[3106]: connect to postbox.fabulous.com[128.242.120.13]:25: Connection timed out

451 Sep 19 08:06:32 ubuntu postfix/smtp[3106]: 5EBB7C5092: to=<renoy29985@gmail.com>, orig_to=<renoy29985>, relay=none, delay    =31, delays=0.01/0/31/0, dsn=4.4.1, status=deferred (connect to postbox.fabulous.com[128.242.120.13]:25: Connection timed     out)

In line 448, it can be seen that the postfix/local API is called and it DELIVERS the mail, since I believe the Relay is Local.

But when we see the line 450, we see the postfix/smtp Server being called and it tries to connect to 'postbox.fabulous.com' and times out. Where is this Address taken from ????

I think, the mail is sent via this server ????

Also, when I try to send the mail to an external Id, the log shows the below failure :

481 Sep 19 08:21:32 ubuntu postfix/smtp[3317]: 19FD5C5095: to=<renoy29985@gmail.com>, relay=none, delay=31, delays=0.05/0.02/    31/0, dsn=4.4.1, status=deferred (connect to postbox.fabulous.com[128.242.120.13]:25: Connection timed out)

Note -> the 'relay' is 'none'. What is meant by 'relay' ??? and the Connection again times out.

Please help.

---

### Post by kimda on 2011-09-20
Relay is the host which sends the email. You can either use a mailserver like your isp to relay your emails for you or let postfix handle the final delivery of the mail. Maybe you can post some more info like the main.cf file of postfix. Is fabulous.com your hosting provider? It tries to connect to deliver the message. 

Did you take a look at the Ubuntu Postfix manual? 
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by dcstar on 2011-09-20
Or the ISP blocks outgoing Port 25 connections as an anti-spam measure.

Very simple to test:

```
telnet smtp.mail.yahoo.com 25
```

If you get a response from the server then it isn't blocked, if you don't then talk to your ISP.

---

### Post by renoy29985 on 2011-09-20
Hi Kimda,

Yep I followed the whole procedure in the manual, and still getting the  same error :-(. Also I verified the main.cf with the manual and it was  alright. Shall I post it ?

 Is fabulous.com your hosting provider? It tries to connect to deliver the message. --> I have no idea :-(
 

Hi DCStar,

I get the response :

renoy29985@ubuntu:/var/log$ telnet smtp.mail.yahoo.com 25
Trying 98.139.212.139...
Connected to smtp.mail.us.am0.yahoodns.net.
Escape character is '^]'.
220 smtp210.mail.bf1.yahoo.com ESMTP
quit
221 Service Closing transmission
Connection closed by foreign host.
renoy29985@ubuntu:/var/log$ telnet smtp.gmail.com 25
Trying 74.125.53.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP ml4sm8142115pbc.0
quit
221 2.0.0 closing connection ml4sm8142115pbc.0
Connection closed by foreign host.

---

### Post by dcstar on 2011-09-21
> **renoy29985 said:**
> Hi Kimda,

Yep I followed the whole procedure in the manual, and still getting the  same error :-(. Also I verified the main.cf with the manual and it was  alright. Shall I post it ?

 Is fabulous.com your hosting provider? It tries to connect to deliver the message. --> I have no idea :-(


The only "procedure" you need to do is:

```
sudo dpkg-reconfigure postfix
```

And you **do not** use dummy entries that are listed in various HOWTOs that are supposed to be replaced by the real values that apply to your system.

---

