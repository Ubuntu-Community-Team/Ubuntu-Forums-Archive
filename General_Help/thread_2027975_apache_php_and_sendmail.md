---
title: "apache php and sendmail"
date: 2012-07-17
forum: General Help
---

### Post by Pedroski55 on 2012-07-17
Hi, 
At home I've been making a webpage. The contact page should accept input from the user, then mail it to me. I am trying  this out on my laptop before I put it on a host.
I have apache2 running on my laptop, configured to use php. Both work fine, I can tell php is working by using a webpage with 

<?php
  phpinfo(); I get lots and lots of info. Among the data is: **sendmail_path	/usr/sbin/sendmail -t -i** , which is where my sendmail is.

I have a script, send_mail.php The part that sends the info is:

mail( "$webmaster_email", "Feedback Form Results",
  $comments, "From: $email_address" );
header( "Location: $thankyou_page" );
}

**Unfortunately, I never receive any mail.** This morning I tried again, here is /var/log/mail

status=bounced (gmail.com)
Jul 17 07:08:05 pedro-bedro postfix/cleanup[2820]: B21136C2148: message-id=<20120716230805.B21136C2148@pedro-bedro>
Jul 17 07:08:05 pedro-bedro postfix/bounce[2823]: 61FF96C2144: sender non-delivery notification: B21136C2148
Jul 17 07:08:05 pedro-bedro postfix/qmgr[1772]: 61FF96C2144: removed
Jul 17 07:08:05 pedro-bedro postfix/qmgr[1772]: B21136C2148: from=<>, size=2024, nrcpt=1 (queue active)
Jul 17 07:08:05 pedro-bedro postfix/local[2824]: B21136C2148:  to=<www-data@pedro-bedro>, relay=local, delay=0.23,  delays=0.07/0.02/0/0.15, dsn=2.0.0, status=sent (delivered to mailbox)
Jul 17 07:08:05 pedro-bedro postfix/qmgr[1772]: B21136C2148: removed

Does anyone have an idea why the mail is not sent?

---

