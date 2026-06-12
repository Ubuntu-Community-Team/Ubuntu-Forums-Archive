---
title: "sendmail - smtp ? set up email"
date: 2011-04-14
forum: General Help
---

### Post by spindler on 2011-04-14
I have recently installed a DRUPAL 7 website  on my Ubuntu server.  I attempted to create a new account on my website and was presented with the following error.

"Unable to send e-mail. Contact the site administrator if the problem persists."

I then tested to see if my server actually sent by creating a php file on the website directory using the following code:

[COLOR=#000000][COLOR=#0000BB]<?php
 
[/COLOR][COLOR=#FF8000]//The standard php mail function
[/COLOR][COLOR=#0000BB]mail[/COLOR][COLOR=#007700]([/COLOR][COLOR=#DD0000]'your-name@your-email-host.com'[/COLOR][COLOR=#007700], [/COLOR][COLOR=#DD0000]'The Subject'[/COLOR][COLOR=#007700], [/COLOR][COLOR=#DD0000]'The email body!'[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000BB]?>

[COLOR=Black]I did not get an email message sent to my address.   Which tells me maybe I do not have my server setup to send emails. ....   Actually I do not know how to set the server up to send emails.  What do I do?  What software package am I looking for?  Could there be something broken?

Can someone please point me to an application I need to install or point me in the right direction to solve this issue?
 
Spindler[/COLOR]
[/COLOR][/COLOR]

---

### Post by r-senior on 2011-04-14
Setting up a full-blown SMTP server can be an overly arduous and error-prone process if all you need is to support automated emails. You might be able to configure your application to use an existing SMTP server or, if it expects a local sendmail, there are always lightweight proxies like msmtp:

[http://msmtp.sourceforge.net/](http://msmtp.sourceforge.net/)

This is in the repositories (package is msmtp) and very simple to set up (only 8 lines of config in my case). I use this on my Webmin installation as the mail transfer agent (MTA) for alerts.

It does mean that you need access to an Internet-hosted SMTP server and mails go outside your domain and back in again, but the advantages could outweigh those slight drawbacks.

---

### Post by spindler on 2011-04-14
Thanks a lot.

I have used g-mail yahoo, etc as an outgoing website email server for my other sites.    I defintely want to set up an external SMTP if I can.  I will look into it.  However Drupal is a different animal and I am still working with the learning curve. 

If I cannot use an external web email service what is the best way to set up a server side SMTP email server?

Thanks,

Spindler

---

### Post by Ralph L on 2011-04-14
I don't really understand your problem, but I sent external email through my server (mail.mchsi.com) by setting the sendmail -f parameter.  For example
sendmail [email]-fmyemailname@mchsi.com[/email] [email]someuser@somewhere.com[/email]

I also set up Thunderbird to receive local email from sendmail.  See [http://ubuntuforums.org/showthread.php?t=1718795](http://ubuntuforums.org/showthread.php?t=1718795) .  Also see [http://ubuntuforums.org/showthread.php?t=1711482](http://ubuntuforums.org/showthread.php?t=1711482) 

Maybe this will be of some help.

Ralph

---

### Post by spindler on 2011-04-14
The issue really is that I do not know anything about sendmail.    Is it an apache2 module?

How do I use it?

---

### Post by Ralph L on 2011-04-15
Well, I'm no expert on anything, so take what I say with a grain of salt.  As far as I know sendmail is just another linux program.  You can install it with Synaptic.  As far as I know it is independent of Apache.  I bumped into sendmail, because fcron/fronq (an improved scheduler program over cron) uses it to notify the user whether or not the scheduled task ran ok.  I had problems with it, because the call to sendmail is built into fcron (I couldn't change it) and my external email provider would not accept a "From" parameter of the form "ralph@ralph-laptop" or "ralph@ralph-laptop.local" (to which fcron set the From field).  However, under Terminal I did "man sendmail" and found the parameter "-f", which allowed me to set the "From" field to my normal external email "From" field and I was able to send an email to myself.  To test sendmail I just entered the following under Terminal:

sendmail [email]-fmyemailname@mchsi.com[/email] [email]myemailname@mchsi.com[/email]
My test message
.

The line with only a "." in it tells sendmail the message is complete and to send it.  Give it a try.  Note:  My email provider is mchsi.com.  Yours, of course will be different.

Ralph

---

### Post by spindler on 2011-04-15
Thanks Ralph,

This is very helpful.  I took a look at what others had to say about sendmail and noticed that Ubuntu 10.10 does not promote it.  The Ubuntu 10.10 server documents point to a bunch of other mail server.  

[https://help.ubuntu.com/10.10/serverguide/C/exim4.html](https://help.ubuntu.com/10.10/serverguide/C/exim4.html)

So I installed exim4 and it appears to work.  Although the configuration is difficult to understand and I get the wrong email header sent.   The server send email out as [email]www-data@server.com[/email] and not a generic email address I want to use. 

I would rather it sent out [email]no-reply@server.com[/email]

I am not sure how to set up Exim4  to do this but I am working on it...

---

