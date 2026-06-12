---
title: "Gmail in Evolution - Problem sending mail"
date: 2009-07-05
forum: General Help
---

### Post by RonB123123 on 2009-07-05
Hi, I'm having a problem sending mail through evolution using Gmail. In my gmail settings, I have enabled pop and imap. Receiving emails is not a problem but sending email gives me this error:

> 
Error while performing operation.

MAIL FROM command failed: 5.0.0 Access denied


My sending email settings are:
> 
Server Type: smtp
Server: smtp.gmail.com
Server requires authentication: Checked
Use secure connection: Tries SSL and TLS
Type: Tries PLAIN and Login
Username: Tries my username with and without @gmail.com 
Remember Password: Checked


I went through the checklist in [gmail's documentation](http://mail.google.com/support/bin/answer.py?hl=en&answer=78775) but it's still not working. Before I used gmail, I used my university address and I had the same issue. Is this a problem in Evolution or am I doing something wrong?

~Ron

---

### Post by DeMus on 2009-07-05
> **RonB123123 said:**
> Hi, I'm having a problem sending mail through evolution using Gmail. In my gmail settings, I have enabled pop and imap. Receiving emails is not a problem but sending email gives me this error:



My sending email settings are:


I went through the checklist in [gmail's documentation](http://mail.google.com/support/bin/answer.py?hl=en&answer=78775) but it's still not working. Before I used gmail, I used my university address and I had the same issue. Is this a problem in Evolution or am I doing something wrong?

~Ron

I use Thunderbird with the settings in the attached picture.

---

### Post by wojox on 2009-07-05
Server: smtp.gmail.com
Flag: server requires authentication
Use Secure Connection: SSL
Fill in Username: username@ gmail.com
Select OK
Done.

Now restart Evolution and see if it all works.

---

### Post by credobyte on 2009-07-05
SMTP port is set to 465 ?

---

### Post by RonB123123 on 2009-07-05
Thanks guys but it still doesn't work.

I'm beginning to think it's evolution. I will try Thunderbird with those settings and will reply back. If it works, I'm never using evolution again and always sticking with the mozilla family. :)

---

### Post by credobyte on 2009-07-05
> **RonB123123 said:**
> Thanks guys but it still doesn't work.

I'm beginning to think it's evolution. I will try Thunderbird with those settings and will reply back. If it works, I'm never using evolution again and always sticking with the mozilla family. :)

Thunderbird does not require any additional configuration for GMail than your email and password - you'll be fine :)

---

### Post by RonB123123 on 2009-11-11
Been using thunderbird for the passed few months and everything works flawlessly! :)

---

