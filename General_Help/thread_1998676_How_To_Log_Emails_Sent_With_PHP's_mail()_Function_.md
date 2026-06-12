---
title: "How To Log Emails Sent With PHP's mail() Function To Detect Form Spam"
date: 2012-06-07
forum: General Help
---

### Post by auraithx on 2012-06-07
Hi all,

I followed this guide here to try and find out if my server was sending out any spam. [http://www.howtoforge.com/how-to-log-emails-sent-with-phps-mail-function-to-detect-form-spam](http://www.howtoforge.com/how-to-log-emails-sent-with-phps-mail-function-to-detect-form-spam)  -- I created the mailtest.php as suggested at the bottom of the guide but nothing appeared in my mail.form. Should using the same exact commands here work in Ubuntu 11.10?

Ta

---

### Post by alanphil on 2012-06-07
The mailtest.php file should be put on your web server. Then access this page in your web browser ([www.yoursite.com/mailtest.php](www.yoursite.com/mailtest.php)). This will execute the script and display 'Mail sent' in your web browser. Do you see this message in your web browser?

The second part of this is the log file should show 'yourname@yourdomain.com','This is a test message subject','This is a test message body'. You can check this by running the following in terminal:

cat /var/log/mail.form

---

### Post by auraithx on 2012-06-08
> **alanphil said:**
> The mailtest.php file should be put on your web server. Then access this page in your web browser ([www.yoursite.com/mailtest.php](www.yoursite.com/mailtest.php)). This will execute the script and display 'Mail sent' in your web browser. Do you see this message in your web browser?

The second part of this is the log file should show 'yourname@yourdomain.com','This is a test message subject','This is a test message body'. You can check this by running the following in terminal:

cat /var/log/mail.form

Yep, the script executes fine.

[http://ablemagazine.co.uk/mailtest.php](http://ablemagazine.co.uk/mailtest.php)

There is nothing in my mail.form after.

---

