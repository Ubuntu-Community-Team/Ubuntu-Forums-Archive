---
title: "trouble with exchange server and evolution mail"
date: 2009-07-13
forum: General Help
---

### Post by jayorinda on 2009-07-13
I have my mail hosted at [www.mailstreet.com]("http://www.mailstreet.com").  i am having trouble setting up my Evolution email account through the exchange server at mailstreet.  For receiving email, i entered as my OWA URL :  [https://mail.mse21.exchange.ms](https://mail.mse21.exchange.ms)

When i try to authenticate the URL, I receive an error that says

The Exchange Server is not compatible with Exchange Connector
The server is running Exchange 5.5.  Exchange connector supports Microsoft Exchange 2000 and 2003 only.

by the way, according to mailstreet, they run Exchange 2007, so i am not sure why evolution comes back saying they run Exchange 5.5.  

i am fairly certain i have the right URL...sounds like their server is not compatible with evolution.  is that really the case?  Any help or suggestions are appreciated.

---

### Post by amlucent23 on 2009-07-13
If I were to venture a guess..

This is the problem..
> **jayorinda said:**
> Exchange connector supports Microsoft Exchange 2000 and 2003 only.

And this is your answer..
> **jayorinda said:**
> they run Exchange 2007


Evolution uses the Webfrontend to communicate. Since this is a complete rewrite for 2007, evolution is pretty useless.

I believe most (ubuntu) users that need to connect to an exchange 2007 server are either using outlook in wine or in a virtual machine.

---

