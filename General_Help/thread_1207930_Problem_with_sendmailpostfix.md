---
title: "Problem with sendmail/postfix"
date: 2009-07-08
forum: General Help
---

### Post by DG2009 on 2009-07-08
Hi 
I am a web developer, i am developing a site locally only, it requires to send verification emails to clients, since php is already configured to use sendmail for sending mails, i tried to install it, but found it's better to install postfix as it provides sendmail interface. So i installed postfix instead.

now the problem is I am able to send mails using postfix command line. but i am unable to send mails using sendmail commandline the command i ve been using is 

sendmail -t -i <mail

mail:

to:myid@gmail.com
from: [EMAIL="abc@abc.com"]abc@abc.com[/EMAIL] //junk mail id
subject:test mail 123

it works!

------

this statement executes fine only but i don't get mail in my gmail account, i tried with other mailid's also but no help, i checked my mail queue using mailq it shows pending mail there but queue becomes empty after few secs, i don't receive mail and i don't get any 553 error.
I am kinda struck here please help me out

regards
deepak

---

### Post by wojox on 2009-07-08
Look in your apache error logs and see what it says.
Did you configure sendmail in your php.ini file?

---

### Post by DG2009 on 2009-07-08
It's not a porblem with php or apache, i am using sendmail standalone from command line, one more thing i tried to send mail to my yahoo account i got 553 error, is it got to do with gmail then or sendmail requires separate configuration, I am totally confused, Please help!

---

### Post by doobie on 2009-07-09
Have you looked at your firewall to make sure that it permits this output? I have had problems kinda like this with iptables.

---

### Post by DG2009 on 2009-07-09
i checked ufw app list it doesnot sendmail, but its inactive too! is that a problem, how can i add app to ufw app list.

---

