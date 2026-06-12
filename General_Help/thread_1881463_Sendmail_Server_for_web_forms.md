---
title: "Sendmail Server for web forms"
date: 2011-11-15
forum: General Help
---

### Post by Audiosears on 2011-11-15
Folks,

Looking for some help figuring out what went wrong / changed recently.  After the upgrade from 11.04 > 11.10, I haven't been able to get Sendmail to properly route email from a web form to my mail server.

On my website, I have a php mail() script that sends a mail to a recipient.  the website is the same server as Sendmail is installed on, and the mail should be relayed (i think) to my mail server on another machine on the same LAN.

I got it working back to the point at which the web form will report success, however the mail does not seem to leave the Sendmail server (it may be being dropped as I am not seeing it populate in the queue either.

After the upgrade, I did notice that php5 was not enabled under apache, and I had to install the appropriate module and restart apache / sendmail.  This is what allowed the php mail() command to execute, but the config files are defaults, not sure if they need to be modified at all.

An excerpt from mail.log is:

***********
Nov 15 14:33:31 server sendmail[23626]: pAFJXVCU023626: Authentication-Warning: server.mydomain.com: www-data set sender to [email]gencontact@mydomain.com[/email] using -f
Nov 15 14:33:31 server sendmail[23626]: pAFJXVCU023626: from=gencontact@mydomain.com, size=1527, class=0, nrcpts=1, msgid=<201111151933.pAFJXVCU023626@server.mydomain.com>, relay=www-data@localhost
Nov 15 14:33:31 server sendmail[23626]: pAFJXVCU023626: to=Webmaster@mydomain.com, delay=00:00:00, mailer=esmtp, pri=31527, dsn=4.4.3, stat=queued
************

The mail does not actually send, nor does it get delivered to any local user.  In the mail() script I'm using -f to change the sender to 'gencontact@mydomain.com'.  I can see that the To: address of 'Webmaster@mydomain.com' is correct, but the 'relay=www-data@localhost' may be the issue.  My intent is to have Sendmail relay to 'mail.mydomain.com' or send it directly, but I'm not sure where the issue lies...

I tried uninstalling / reinstalling sendmail, loading older sendmail.cf / submit.cf files with no change.

---

### Post by Audiosears on 2011-11-15
Folks,

Well, sort of a copout perhaps, but I noticed a thread for Nullmailer, which is exactly what I need for this situation (SMTP only from the web form to my email server).

I followed the guide at [this]("http://ubuntuforums.org/showthread.php?t=56077&highlight=sendmail+php") post and it worked like a charm.  I already have a few SMTP accounts on my mail server I use elsewhere to send things like email alerts, and I used that information in the config file.

I then tried to send mail from my PHP form, and like magic, it works again :D

---

