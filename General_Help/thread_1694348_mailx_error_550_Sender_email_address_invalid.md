---
title: "mailx error 550 Sender email address invalid"
date: 2011-02-24
forum: General Help
---

### Post by JeanCr on 2011-02-24
Hi,
I'm trying to send mail from the commandline. It does not work and in /var/log/mail.err I read 'Feb 24 13:59:11 maria sSMTP[7022]: 550 Sender e-mail address invalid '.

I changed /etc/mailname from the computername 'maria' to my email address but it does not help.

Command line I use is: mailx [email]my@email.com[/email] < ./somefile
Smtp server is set in /etc/ssmtp/ssmtp.conf: mailhub=smtp.ziggo.nl

Any idea?
Thanks

Edit, found solution here: [http://ubuntuforums.org/showthread.php?t=780509](http://ubuntuforums.org/showthread.php?t=780509)

---

