---
title: "Can't login to Gtalk with Empathy"
date: 2009-11-18
forum: General Help
---

### Post by conradtheart on 2009-11-18
Hi,

My Google Account is not a @gmail.com account, but @technologyheaven.com I bought this domain via Google and use it as my Gtalk login. I've had problems login in with Empathy before, but for the last few months it just refuses to log in. It gives me login detail errors and even network errors.

So my question to someone using a Google Account with a login other than @gmail.com is, how do you configure Empathy (or Pidgin) to login?

Thank you.

---

### Post by lephio on 2009-11-24
same to me :/

---

### Post by chaitanya.bendre on 2009-11-26
same problem here........

---

### Post by conradtheart on 2009-11-27
Ok so I got it sorted. Here is how.

Add a jabber account and enter your full email address in the Login ID field. Enter your password and expand the advanced section. 

Next, check "Encryption required (TSL/SSL)" and "Ignore SSL certificate errors".

In the server box enter "talk.google.com" and make sure the port is set at 5222.

That should be it. Let me know if it works for you too.

---

### Post by libertao on 2010-07-13
Just in case anyone comes across this thread like I did -- my mistake was leaving off the "@gmail.com" in the username field (I accidentally left it off because you never need it to log in to google accounts in a browser).

---

