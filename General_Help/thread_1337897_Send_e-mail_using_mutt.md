---
title: "Send e-mail using mutt?"
date: 2009-11-25
forum: General Help
---

### Post by Koalano on 2009-11-25
Hi guys,

At home I can use mutt to send an email without any problem. 

For example the following command works fine:

```
$ mutt -s "Test mail" -a  /tmp/file.tar.gz  vivek@nixcraft.co.in  < /tmp/mailmessage.txt
``` Where,

- [EMAIL="vivek@nixcraft.co.in"]vivek@nixcraft.co.in[/EMAIL] - is the recipient
- /tmp/mailmessage.txt - is  the main body of the e-mail (read message from the file "mailmessage.txt")
- /tmp/file.tar.gz - is an attachment (with option -a)
- "Test mail" - is a subject line (option -s)


However I can't do the same thing at my office which uses proxy to connect to the internet. 



(I use exim4 to send messages through GMail, and when setting up exim4 I followed the guide at the website [http://wiki.debian.org/GmailAndExim4](http://wiki.debian.org/GmailAndExim4))


Please help me to solve the problem.


Thanks and regards,


Koalano.

---

### Post by dcstar on 2009-11-25
> **Koalano said:**
> Hi guys,

At home I can use mutt to send an email without any problem. 
.........
However I can't do the same thing at my office which uses proxy to connect to the internet. 
..........
Please help me to solve the problem.


If your office has blocked SMTP, then that is that.

Ask your office to allow SMTP access, there is nothing else you can do.

---

### Post by Koalano on 2009-11-25
> **dcstar said:**
> If your office has blocked SMTP, then that is that.

Ask your office to allow SMTP access, there is nothing else you can do.

Hi, how do I know if the SMTP access is blocked without asking the administrator? Is there any command to check this from my computer?

Thanks.

---

