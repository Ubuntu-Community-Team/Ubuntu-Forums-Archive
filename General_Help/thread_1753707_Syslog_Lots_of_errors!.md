---
title: "Syslog Lots of errors!"
date: 2011-05-09
forum: General Help
---

### Post by ubila on 2011-05-09
Hello,
Running Ubuntu Server 11.04

Im getting these error messages recorded in /var/log/syslog, 15 every second!!!

May  9 08:15:35 servername sm-mta[32604]: p451e1nD003345: to=<www-data@servername.co.nz>, ctladdr=<www-data@servername.co.nz> (33/33), delay=3+18:35:34, xdelay=00:00:00, mailer=local, pri=49171147, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL^C
 
What do they mean?

Thanks

---

### Post by matt_symes on 2011-05-09
Hi

> **ubila said:**
> Hello,
Running Ubuntu Server 11.04

Im getting these error messages recorded in /var/log/syslog, 15 every second!!!

May  9 08:15:35 servername sm-mta[32604]: p451e1nD003345: to=<www-data@servername.co.nz>, ctladdr=<www-data@servername.co.nz> (33/33), delay=3+18:35:34, xdelay=00:00:00, mailer=local, pri=49171147, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL^C
 
What do they mean?

Thanks

sm-mta is the 'send mail' mail transport agent. It looks like it's failing to send messages for some reason and deferring sending the mail.

Kind regards

---

### Post by ubila on 2011-05-09
Well, it seems odd that sendmail is trying to send 15 messages per second?

Could my server be compromised with a email spam bot?
How can I track down what is trying to send all these emails?

Thanks

---

### Post by ubila on 2011-05-09
Here is a screenshot of top showing sendmail at 4% cpu.

If i do a cat /var/mail/root | grep '10 May' (today)
It seems this mail is trying to be sent every 10mins 


root@hostname:# cat /var/mail/root | grep '10 May'
        Tue, 10 May 2011 00:06:01 +1200
Date: Tue, 10 May 2011 00:06:01 +1200
Last-Attempt-Date: Tue, 10 May 2011 00:06:01 +1200
        Tue, 10 May 2011 00:16:03 +1200
Date: Tue, 10 May 2011 00:16:03 +1200
Last-Attempt-Date: Tue, 10 May 2011 00:16:03 +1200
        Tue, 10 May 2011 00:26:02 +1200
Date: Tue, 10 May 2011 00:26:02 +1200
Last-Attempt-Date: Tue, 10 May 2011 00:26:02 +1200
        Tue, 10 May 2011 00:36:02 +1200
Date: Tue, 10 May 2011 00:36:02 +1200
Last-Attempt-Date: Tue, 10 May 2011 00:36:02 +1200
        Tue, 10 May 2011 00:46:02 +1200
Date: Tue, 10 May 2011 00:46:02 +1200
Last-Attempt-Date: Tue, 10 May 2011 00:46:02 +1200
        Tue, 10 May 2011 00:56:03 +1200
Date: Tue, 10 May 2011 00:56:03 +1200
Last-Attempt-Date: Tue, 10 May 2011 00:56:03 +1200
        for <root@hostname.co.nz>; Tue, 10 May 2011 01:00:15 +1200
        for root; Tue, 10 May 2011 01:00:15 +1200
Date: Tue, 10 May 2011 01:00:15 +1200
        Tue, 10 May 2011 01:06:03 +1200
Date: Tue, 10 May 2011 01:06:03 +1200
Last-Attempt-Date: Tue, 10 May 2011 01:06:03 +1200
        Tue, 10 May 2011 01:16:04 +1200
Date: Tue, 10 May 2011 01:16:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 01:16:04 +1200
        Tue, 10 May 2011 01:26:03 +1200
Date: Tue, 10 May 2011 01:26:03 +1200
Last-Attempt-Date: Tue, 10 May 2011 01:26:03 +1200
        Tue, 10 May 2011 01:36:04 +1200
Date: Tue, 10 May 2011 01:36:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 01:36:04 +1200
        Tue, 10 May 2011 01:46:04 +1200
Date: Tue, 10 May 2011 01:46:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 01:46:04 +1200
        Tue, 10 May 2011 01:56:04 +1200
Date: Tue, 10 May 2011 01:56:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 01:56:04 +1200
        Tue, 10 May 2011 02:06:04 +1200
Date: Tue, 10 May 2011 02:06:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 02:06:04 +1200
        Tue, 10 May 2011 02:16:04 +1200
Date: Tue, 10 May 2011 02:16:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 02:16:04 +1200
        Tue, 10 May 2011 02:26:04 +1200
Date: Tue, 10 May 2011 02:26:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 02:26:04 +1200
        Tue, 10 May 2011 02:36:04 +1200
Date: Tue, 10 May 2011 02:36:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 02:36:04 +1200
        Tue, 10 May 2011 02:46:04 +1200
Date: Tue, 10 May 2011 02:46:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 02:46:04 +1200
        Tue, 10 May 2011 02:56:04 +1200
Date: Tue, 10 May 2011 02:56:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 02:56:04 +1200
        Tue, 10 May 2011 03:06:04 +1200
Date: Tue, 10 May 2011 03:06:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 03:06:04 +1200
        Tue, 10 May 2011 03:16:04 +1200
Date: Tue, 10 May 2011 03:16:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 03:16:04 +1200
        Tue, 10 May 2011 03:26:04 +1200
Date: Tue, 10 May 2011 03:26:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 03:26:04 +1200
        Tue, 10 May 2011 03:36:03 +1200
Date: Tue, 10 May 2011 03:36:03 +1200
Last-Attempt-Date: Tue, 10 May 2011 03:36:03 +1200
        Tue, 10 May 2011 03:46:04 +1200
Date: Tue, 10 May 2011 03:46:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 03:46:04 +1200
        Tue, 10 May 2011 03:56:04 +1200
Date: Tue, 10 May 2011 03:56:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 03:56:04 +1200
        Tue, 10 May 2011 04:06:04 +1200
Date: Tue, 10 May 2011 04:06:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 04:06:04 +1200
        Tue, 10 May 2011 04:16:04 +1200
Date: Tue, 10 May 2011 04:16:04 +1200
Last-Attempt-Date: Tue, 10 May 2011 04:16:04 +1200
        Tue, 10 May 2011 04:26:05 +1200


I really need to find what is trying to send this mail! 
Has anyone got any ideas on how to track this down!

Thanks

---

### Post by matt_symes on 2011-05-09
Hi

If you can get to this URL have a look at the section on ex_tempfail

[http://docstore.mik.ua/orelly/networking/sendmail/ch36_05.htm](http://docstore.mik.ua/orelly/networking/sendmail/ch36_05.htm)

Kind regards

---

### Post by ubila on 2011-05-09
**My /var/spool/mqueue is absolutly PACKED with messages.**

---

### Post by ubila on 2011-05-09
> **matt_symes said:**
> Hi

If you can get to this URL have a look at the section on ex_tempfail

[http://docstore.mik.ua/orelly/networking/sendmail/ch36_05.htm](http://docstore.mik.ua/orelly/networking/sendmail/ch36_05.htm)

Kind regards

Hi, thanks for your reply.
Im not sure that i understand this completely. It seems to be saying that the message failure will queue to resend?

As i posted, my mail queue has ALOT of mail in there, and when i try run sendmail -q to remove it, it just adds MORE mail into the queue. 

Really getting worried here. Does this look like an intrusion?
Thanks

---

### Post by matt_symes on 2011-05-09
Hi

Well it wants to send the mail here: [EMAIL="www-data@servername.co.nz"]www-data@servername.co.nz[/EMAIL]. I might be wrong but i am wondering if something is misconfigured or not configured.

What services do you have running on your server ?

EDIT:

> Does this look like an intrusion?

I don't think so. As i said it looks like something is mis/not configured correctly.

Kind regards

---

### Post by ubila on 2011-05-09
> **matt_symes said:**
> Hi

Well it wants to send the mail here: [email]www-data@servername.co.nz[/email]. I might be wrong but i am wondering if something is misconfigured or not configured.

What services do you have running on your server ?

Kind regards

Just normal webserver stuff.
Apache2, sendmail, proftp, mysql 

I just deleted all the mail in the queue by doing this:
rm -f /var/spool/mqueue

This seemed to remove all the mail in there... for now i guess. Ill just have to see in 10mins time if it adds more.

---

### Post by matt_symes on 2011-05-09
Hi 

Running nslookup did not return anything for the domain

```
matthew@matthew-laptop:~$ nslookup servername.co.nz
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find servername.co.nz: NXDOMAIN

```

Kind regards

---

### Post by matt_symes on 2011-05-09
Hi
> 
Just normal webserver stuff.
Apache2, sendmail, proftp, mysql 

I just deleted all the mail in the queue by doing this:
rm -f /var/spool/mqueue

You could grep your hard drive looking for servername.co.nz and see what it finds. I expect it will be in a configuration file somewhere.

I cannot be 100% sure it's malware. If you are really worried unplug your pc from the network.

Kind regards

---

### Post by ubila on 2011-05-09
> **matt_symes said:**
> Hi 

Running nslookup did not return anything for the domain

```
matthew@matthew-laptop:~$ nslookup servername.co.nz
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find servername.co.nz: NXDOMAIN

```

Kind regards

Hi this is not the actual domain, i edited the output before posting.

If i do a nslookup i get back :

Server:  60.234.1.1
Address: 60.234.1.1#53

Non-authoritative answer:
Name: servername
Address: server ip address

thanks

---

### Post by ubila on 2011-05-09
> **matt_symes said:**
> Hi


You could grep your hard drive looking for servername.co.nz and see what it finds. I expect it will be in a configuration file somewhere.

I cannot be 100% sure it's malware. If you are really worried unplug your pc from the network.

Kind regards

Well i do know that no mail is sending out of my network, as i can look at the counters on my access-list for smtp. So it seems nothing is leaving the network

---

### Post by ubila on 2011-05-09
After about 20mins, two more mail entries are back in the mail queue

root@servername:/var/spool/mqueue# ls
dfp4A0A1K9019276  qfp4A0A1K9019276

So. I guess just removing them is not going to solve this problem. You suggested to grep my HDD looking for matches of my server name (in config files?)

How could i do this? (Im not the best with good ol grep :P )

Thanks

---

### Post by ubila on 2011-05-09
Here is the cat of the latest two files:

root@servername:/var/spool/mqueue# cat dfp4A0A1K9019276
Error: SiteDomain parameter not defined in your config/domain file. You must edit it for using this version of AWStats.
Setup ('/etc/awstats/awstats.conf' file, web server or permissions) may be wrong.
Check config file, permissions and AWStats documentation (in 'docs' directory).


root@servername:/var/spool/mqueue# cat qfp4A0A1K9019276
V8
T1304986201
K1304986434
N2
P121148
I251/0/393333
MDeferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Fbs
$_localhost.localdomain [127.0.0.1]
$rESMTP
$**sservername.co.nz**
${daemon_flags}
${if_addr}127.0.0.1
S<www-data@servername.co.nz>
A<>
MDeferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
rRFC822; [email]www-data@sservername.co.nz[/email]
RPFD:<www-data@servername.co.nz>
H?P?Return-Path: <g>
H??Received: from servername.co.nz (localhost.localdomain [127.0.0.1])
 by servername.co.nz (8.14.4/8.14.4/Debian-2ubuntu1) with ESMTP id p4A0A1K9019276
 for <www-data@servername.co.nz>; Tue, 10 May 2011 12:10:01 +1200
H?x?Full-Name: www-data
H??Received: (from www-data@localhost)
 by spiders.wmedia.co.nz (8.14.4/8.14.4/Submit) id p4A0A11h019275
 for www-data; Tue, 10 May 2011 12:10:01 +1200
H??Date: Tue, 10 May 2011 12:10:01 +1200
H??Message-Id: <201105100010.p4A0A11h019275@servername.co.nz>
H??From: [email]root@servername.co.nz[/email] (Cron Daemon)
H??To: [email]www-data@servername.co.nz[/email]
H??Subject: Cron <www-data@servername> [ -x /usr/share/awstats/tools/update.sh ] && /usr/share/awstats/tools/update.sh
H??Content-Type: text/plain; charset=ANSI_X3.4-1968
H??X-Cron-Env: <SHELL=/bin/sh>
H??X-Cron-Env: <HOME=/var/www>
H??X-Cron-Env: <PATH=/usr/bin:/bin>
H??X-Cron-Env: <LOGNAME=www-data>

---

### Post by ubila on 2011-05-09
OK from this i think its awstats that is causing the issue.
How can i completely remove awstats? 

I tried :
dpkg -r awstats psa-awstats-configurator

But it still seems there are config files around

thanks

---

### Post by matt_symes on 2011-05-09
Hi

Try

```
sudo apt-get remove --purge awstats
```

That might work.

Kind regards

---

### Post by ubila on 2011-05-09
> **matt_symes said:**
> Hi

Try

```
sudo apt-get remove --purge awstats
```

That might work.

Kind regards

Hi yes that did work.
And no more mail errors are queuing. Seems awstats was incorrectly configured and sending mass mails.

I did not need awstats so instead of fixing it, removing it was the option.

Thanks for all your help and direction.

---

