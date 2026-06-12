---
title: "PHP FormMail Question"
date: 2010-05-13
forum: General Help
---

### Post by JWilkinson on 2010-05-13
So, I'm designing this website for a business and they are wanting a form that people can fill out to submit information on a job they want a bid done on. Since I do not know how to code in PHP I just downloaded a little script to do the work and configured it to my liking. Now, my issue. The script works perfectly except one thing, the emailing part and I've deduced it down to the fact that it uses sendmail to send the email to us. That's all well and good but I read that sendmail is a security hazard waiting to happen so here is my question. Eventually we want to have both a web server/mail server all set up at once on the same machine but we're going one step at a time and I'm working on this, anyway, could PostFix be used to do the same thing that they are trying to use SendMail to do? If so, how or have any suggestions for scripts to accomplish what I am working on? I've just recently gotten into Ubuntu/PHP/Web Servers and most anything else beyond basic HTML script, Java/VB or whatever so be easy on me!

---

### Post by alienprdkt on 2010-05-13
well don't know exactly what you want since you don't have setup a mail server yet, and are not wanting to attempt that long process just yet either.

But if its a form you want to create. This is the place for php css and many others...

[http://www.w3schools.com/](http://www.w3schools.com/)

for a mail server heres what I am halfway with building...

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) shows everything you need for a mail server! incl. spam, virus detection as well as your ssl cert.

---

### Post by JWilkinson on 2010-05-13
Ah, so w3schools answered a question as to a possibility of why it isn't working. Have to specify a path for the program. Now that we have that established, does sendmail -have- to be used in this circumstance or can something else be used instead? I don't want to leave any security holes out there if I can avoid it. If it does have to be used, later on when I go in to set up the mail server will it conflict with PostFix or whatever other program I decide to use for it?

---

