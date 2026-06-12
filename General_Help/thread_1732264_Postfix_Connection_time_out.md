---
title: "Postfix Connection time out"
date: 2011-04-18
forum: General Help
---

### Post by htorbov on 2011-04-18
Hi! I'm trying to send an e-mail to my g-mail address using Postfix on Ubuntu server but when I check the postq, it shows me that the connection to gmail on port 25 is timed out. I have a router that forward port 25 to the machine.. I don't know what is going on :( please help me..

---

### Post by falko on 2011-04-18
Please make sure that your server isn't blacklisted: [http://www.mxtoolbox.com/blacklists.aspx](http://www.mxtoolbox.com/blacklists.aspx)
If you have a dynamic IP, it most probably is. In that case you should set up relaying: [http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver)

---

### Post by htorbov on 2011-04-18
Hi, thanks for the fast reply!

Last week I was trying to send e-mails with Mailman (list includes only my gmail address) because I have a webdesign company and I want to send e-mails to my customers (in the future).. everything was okay.. maybe I mistaked something because now I saw that I'm blacklisted:
Tiopan	 LISTED	Return codes were: 127.0.0.2
!?!? I just send them e-mail..

This is rediculous I send e-mail only to my address to check is it everything okay :(

---

