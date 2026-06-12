---
title: "Looking for a mail server with a SQL backend for accounts"
date: 2009-12-05
forum: General Help
---

### Post by DemonBob on 2009-12-05
Ok guys, 

Here's a question, I am looking for a mail server with a SQL backend for user accounts. We use software to dispatch tech's in house some of the techs are outsource. What we want to start doing is anytime we signup a tech they get a free email address from one of our subdomains. 

Basically i am going to write code to bridge the account information and inset it into the mail server DB any time a account is created. I would like a solution that can use MS SQL if possible, as our in house software currently uses it, and it would be easier to bridge the information across. If not, i'll have to write a xml bridge and parse the information from a share. 

I consider myself an experienced Linux User, but needless to say, I still have only Managed an Exchange mail server environment, so i do not know all the mail server possibilities with Linux. 

Yes i know i could do this with exchange, but i would like to keep their email separate from the actual corporate email. Not to mention I have been wanting to setup a Linux mail server in a corporate environment for ages :)  

If anyone can point me in the right direction i would appreciate it.

---

### Post by Bruce H on 2009-12-05
Try [Postfix]("https://help.ubuntu.com/community/Postfix"). It [integrates]("http://www.postfix.org/MYSQL_README.html") with MySQL nicely, and there is also a good webmin module for it, making administration easy.

---

### Post by Bruce H on 2009-12-05
You might also look at this [handy tutorial]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto") for a complete Postfix solution for enterprises.

---

