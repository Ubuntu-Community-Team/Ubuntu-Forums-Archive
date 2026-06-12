---
title: "Mail Server unreachable, please help"
date: 2009-07-19
forum: General Help
---

### Post by kukoobash on 2009-07-19
hello, I have been trying to setup a mail server in ubuntu using this tutorial: [http://flurdy.com/docs/postfix/index.html](http://flurdy.com/docs/postfix/index.html)

I have completed the basic configurations (I havent reached the extend part yet)

So, I have used telnet and the following works:
 - send email to gmail 
 - send mail to itself
 - forward the mail it receives (I have forwarded the mail I receive to an external account for testing purposes)


So my problem is I cannot send mail from gmail, I get '530 530 5.7.1 Invalid Address'.

All of what I have tried is:
-  I have tried pinging my mail server from another pc on the same network, cant find the server. 
- I disabled the router's firewall, forwarded the port and set up my mail server as an exposed host.
- Disabled shorewall on my mail server.
- Changed the shorewall policies to allow everything in.

At each of the above steps I tried sending an email from gmail to my mail server and I still get the same error.

I am really not sure what is happening, and am clueless of what to do. Any help is greatly appreciated. Thank you in advance.

---

