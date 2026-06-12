---
title: "Send html email using PHP with Gmail"
date: 2011-02-25
forum: General Help
---

### Post by bramvanvliet on 2011-02-25
Hi all, I have a Ubuntu 10.10 installation, with a working PHP environment.
Now I would like to try sending mail using PHP with Gmail.
I have this already working in combination with exim4.
But right now I can only send plain text messages, and I would like to send my mails with html format. Is it even possible to send html mails with exim4?
Or do I need another setup, like suggested in the following blogpost?
[http://deepakssn.blogspot.com/2006/06/gmail-php-send-email-using-php-with.html](http://deepakssn.blogspot.com/2006/06/gmail-php-send-email-using-php-with.html)

This blogpost is already a few years old, so perhaps there are better solutions around!
I hope you guys can help me around.

---

### Post by lncoll on 2011-02-25
The best is you read this page from php.net, in the examples there is a way to send simple html messages:

[http://php.net/manual/en/function.mail.php]("http://php.net/manual/en/function.mail.php")

Or better than the mail function you also can use Pear::Mail_Mime

[http://pear.php.net/package/Mail_Mime]("http://pear.php.net/package/Mail_Mime")

Hope this helps.

---

