---
title: "command line &quot;mail&quot; not sending mail to my email account."
date: 2009-07-09
forum: General Help
---

### Post by doobie on 2009-07-09
I have Ubuntu Server 9.04 installed on a home network server machine that I use to backup my data. I have installed Postfix following this tutorial: [https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix").  I have it setup so that my local user can send email to itself and it shows up as new mail in my "~/Maildir/new/" directory.  However, I am unable to send mail to my personal gmail account using: 
```
mail -s "Test Subject" my_email@gmail.com < test_message
```
where "test_message" is a text file containing the body of the email. I do not get an error message when I execute this command. I have even set my iptables to allow everything in/out, but it still will not show up in my gmail inbox.  My goal is to have logwatch mail logs to my gmail account at some interval.  Any ideas?  Thanks in advance...

---

### Post by slugmax on 2009-07-09
What does /var/log/mail.log show you for these emails? I would try just tailing that file during a send attempt.

Incidentally, if you install mailx, and use the '-v' switch with it, it will mail a delivery status report to the local user account sending the mail.

---

