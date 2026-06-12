---
title: "Problem sending emails from the terminal"
date: 2012-05-21
forum: General Help
---

### Post by Lisandro1987 on 2012-05-21
I instaled 'mailx' running:

         yum install mailx
 

After that, I try to send an email running:

        echo "Body" | mail -s "Subject" [EMAIL="mail@mydomain.com"]mail@mydomain.com[/EMAIL] [EMAIL="mail@gmail.com"]mail@gmail.com[/EMAIL]
 

I received the email in my Gmail account, but i didn't received that in my MyDomain account (where MyDomain are the accounts from my sites web).


What can I do? Where is the log of this app? Thanks so much!

---

### Post by Lisandro1987 on 2012-05-21
I'd resolved that changing the hostname from 'mysite' to 'mysite.com'. Thanks!

---

