---
title: "Error Registering Twiki User"
date: 2009-11-03
forum: General Help
---

### Post by toleolu on 2009-11-03
I installed Twiki from Synaptic (Ubuntu 9.04)

No errors on install but when I go to the Main Twiki page to register as a user, it errors:

**Error registering new user **

  Internal error when sending email to [EMAIL="myemail@my.com"]myemail@my.com[/EMAIL]. 
 Please contact 0. 
 You have **not** been registered. 





Anyone ever run into this???

---

### Post by Zoanie on 2009-11-26
I just completed the same synaptic install on Ubuntu 9.10, and I have the same problem.  It is a new install so perhaps the email client needs configuring.  Hmm...

---

### Post by toleolu on 2009-11-26
The problem wasn't the mail client, it was the mail server. Or more specifically, the lack of one. I installed sendmail on the computer running twiki and that allowed the validation emails to be sent when a user registers.

If you don't want to install a mail server on your computer, I did come across some posts on how to disable that feature so users could register without having to recieve the email. I forget where that is but if you Google "disable user validation email + twiki" you shouldn't have any trouble finding it.

Good Luck

---

