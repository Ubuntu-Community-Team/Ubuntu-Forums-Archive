---
title: "email on command line"
date: 2006-06-13
forum: General Help
---

### Post by evaristegalois on 2006-06-13
forgive my naivity but it seems like I am trying to do something that is out of my league. I want to send emails on the command line, e.g. so that I can send timed emails to myself via cron. It seems that I need to install a program such as postfix in order to do that (which I did). Having postfix installed, how can I now send an email on the command line? Do I need to do any telnetting? What is the syntax of sending an email (I could not figure out what postfix means by words such as "data" or "rcpt")? All I have at this point is my own domainname which allows me to send and receive emails on a mail client (Thunderbird). Shouldn't that be enough to send an email via command line? 

--evaristegalois

---

### Post by echo $USER on 2006-06-13
Here is the man page for the > mailcommand.

[http://www.linuxcommand.org/man_pages/mail1.html](http://www.linuxcommand.org/man_pages/mail1.html)

But i think you can only send/recieve email from your own domain through the terminal, but i could be wrong.

---

### Post by evaristegalois on 2006-06-15
here is the solution to my problem. postfix is very hard to configure, to be sure. there is, however, a little application which does exactly what I want with minimum fuss. it's called sendEmail and can be downloaded here:

[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

---

