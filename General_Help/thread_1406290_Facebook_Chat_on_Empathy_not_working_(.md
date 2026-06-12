---
title: "Facebook Chat on Empathy not working :("
date: 2010-02-13
forum: General Help
---

### Post by jman6495 on 2010-02-13
so , recently facebook allowed facebook chat using jabber ,
i am trying to configure it and have run into some problems

so heres what i have got:

Username : [email]jman6495@chat.facebook.com[/email]  (i have also tried just jman6495)
password : my facebook password
enabled : yeah

ADVANCED :

Encryption Reguired (SSL/TLS) :No
ignore ssl certificate errors : no
resource : (nothing)
priority : 0

Override server settings

Server : chat.facebook.com
port:5222
use old ssl : no

and i get either :

Authentication Failed with the username [email]jman6495@chat.facebook.com[/email]
or Network Error with the username jman6495


i have configured jman6495 as my username in facebook



help appreciated

   ~jman6495

---

### Post by Konrad Ansehelm on 2010-02-16
It works easiest if you make a new Google Talk account.

> **NightHawk_UK said:**
> 
Create a Google Talk account.

  Login ID: [EMAIL="fbusername@chat.facebook.com"]fbusername@chat.facebook.com[/EMAIL]
Password: fb_password

Server: chat.facebook.com
    Port: 5222

Only 'Enabled' should be ticked.

Empathy connected straight away using this for me.

Then i found I could only send but not receive messages so i added a Jabber account (reuse existing) with all the same as above and it connected properly, i then removed the Google Talk account and it works perfectly now.

---

