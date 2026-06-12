---
title: "how to use mailutil"
date: 2011-04-20
forum: General Help
---

### Post by testarap on 2011-04-20
I want to use mailutil to send mail command line. but unable to send Internet mail. please tell me how to configure it to send mail?:confused:

---

### Post by Gareth_2007 on 2012-11-29
1st - [http://yaui.me/postfix-gmail-smtp-server-relay-ubuntu/](http://yaui.me/postfix-gmail-smtp-server-relay-ubuntu/)

2nd - sudo apt-get install mailutils

to test - echo "Call from customer X" | mail -s "Call from customer X" [email]test@test.com[/email]

---

### Post by Parker32 on 2012-11-30
Afaik "mail" utility checks mails at the location given with the MAIL environment variable. Try this command: MAIL=/home/USER/Maildir/ mail (for sure, replace USER with something meaningful & valid). If that works, it seems that you should set MAIL variable you can do it in your bash profile / rc file for example. You can check the content of your current MAIL variable with: echo $MAIL

---

