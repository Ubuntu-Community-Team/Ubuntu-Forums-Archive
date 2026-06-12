---
title: "Cannot send email with ssmtp"
date: 2011-09-25
forum: General Help
---

### Post by slashwannabe94 on 2011-09-25
Hey all,
I can't seem to send anything with ssmtp. My credentials in the /etc/ssmtp are all correct by the way. 

echo "hello" | mail -v -s "test" myemail.com
[<-] 220 mx.google.com ESMTP en9sm28104385wbb.24
[->] EHLO my-desktop
[<-] 250 ENHANCEDSTATUSCODES
[->] STARTTLS
[<-] 
send-mail: Cannot open smtp.gmail.com:587

any ideas people? 

Thanks, 
SlashWannabe94

---

### Post by andrew.46 on 2011-09-25
I have not used ssmtp with Gmail for some time, having converted to msmtp a while back. Perhaps you could use some of the information on this page:

Using Mutt with Gmail
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

In particular the msmtp and certs setup.

---

