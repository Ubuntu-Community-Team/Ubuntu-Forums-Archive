---
title: "can't send mail from localhost"
date: 2012-01-12
forum: General Help
---

### Post by webcomm on 2012-01-12
I'm trying to send mail from localhost using the PHP mail function.  My test script, which is simply a call to the mail function, works fine on my host, but not on my computer (localhost).  

I first tried sendmail, by editing the sendmail_path in php.ini like so:

sendmail_path = /usr/sbin/sendmail -t

That didn't seem to work.  No email was received at my gmail account where I had tried to send the email.  I checked the inbox and the spam folder.  There was no error in my php log.  In the mail log, I saw entries like this...

Jan 12 09:58:04 ubuntu sendmail[3438]: q0CEw3DD003438: to=myemailaccount@gmail.com, ctladdr=www-data (33/33), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30083, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (q0CEw38b003439 Message accepted for delivery)

...where [email]myemailaccount@gmail.com[/email] is my gmail address.  I don't know how to read a mail log, but that entry looks pretty good to me, I suppose.  However, I'm not seeing the email in my gmail account, and I've now waited a good while for it to show up.

What might I be missing?  

Apologies if this is off topic for the ubuntu forum.  I am using ubuntu, though I don't presume my problem here lies in how I'm using ubuntu.  Not really sure.

---

### Post by tt8 on 2012-01-22
Try this site:
[http://sourcelibrary.org/2011/08/29/how-to-set-up-the-php-mail-function-on-a-ubuntu-linux-lamp-server/]("http://sourcelibrary.org/2011/08/29/how-to-set-up-the-php-mail-function-on-a-ubuntu-linux-lamp-server/")

I followed the steps, and it worked for me.  You have to have LAMP installed first.  And one other thing:  When installing Postfix, click ok to everything, except 'System Mail Name."  You set it to localhost.

---

### Post by dcstar on 2012-01-22
> **webcomm said:**
> I'm trying to send mail from localhost using the PHP mail function.  My test script, which is simply a call to the mail function, works fine on my host, but not on my computer (localhost).  
..........
Jan 12 09:58:04 ubuntu sendmail[3438]: q0CEw3DD003438: to=myemailaccount@gmail.com, ctladdr=www-data (33/33), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30083, **relay=[127.0.0.1] [127.0.0.1]**, dsn=2.0.0, stat=Sent (q0CEw38b003439 Message accepted for delivery)

...where [email]myemailaccount@gmail.com[/email] is my gmail address.  I don't know how to read a mail log, but that entry looks pretty good to me, I suppose.  However, I'm not seeing the email in my gmail account, and I've now waited a good while for it to show up.

What might I be missing?  


You do **not** "relay" through the same server you are sending from!

A "relay" is an external SMTP server.

---

