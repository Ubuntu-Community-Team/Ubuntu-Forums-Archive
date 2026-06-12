---
title: "Postfix+Php issue in Ubuntu"
date: 2011-08-26
forum: General Help
---

### Post by titubeta on 2011-08-26
Hello,
I am developing a web application (Php+Apache+Postgres on  Ubuntu) where registered users can send emails to the admin and vice  versa using forms. I have postfix's sendmail installed as MTA. The problem is php mail command  isnt sending/receiving any mail. The registered users can have any  email id e.g. [EMAIL="user1@abc.com"]user1@abc.com[/EMAIL], [EMAIL="user2@xyz.com"]user2@xyz.com[/EMAIL] and admin can be  [EMAIL="admin@example.com"]admin@example.com[/EMAIL]. The idea is that users can send email to admin (and vice versa) using my web application form.
  I earlier tried ssmtp MTA but using that if i provide admin's email  (e.g. gmail's authentication), then admin can contact users but I could  not figure out the other way around communication (from users to admin  because it is not necessary that all users have gmail id).
  Can you guys throw some light on how to solve this problem such that  any user with any email id can contact the admin or vice versa. Communication among users is not allowed.
 What  would be the best steps to address this problem? Currently I am using my local machine (localhost) as test server. Thanks for your support.
  

**[B]Regards**[/B]
**[B]Shrz**
[/B]

---

### Post by jshayden on 2011-08-26
I typically use the [PHPMailer]("http://phpmailer.worxware.com/") library for sending mail via PHP.  It's quite powerful and easy to use.

---

### Post by titubeta on 2011-08-26
Thanks. Do you think PhpMailer can solve the problem I am encountering right now? In simple words, what I want is that using html form two users can send emails to each other and the mails are delivered to their boxes and all of this is wrapped up inside php!

---

