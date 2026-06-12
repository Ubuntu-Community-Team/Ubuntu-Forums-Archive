---
title: "Evolution and MS Exchange"
date: 2011-04-20
forum: General Help
---

### Post by mawe3661 on 2011-04-20
Hi,

I am trying to configure evolution to work with MS Exchange but cannot get it to work. I also have an android phone which is dead easy to configure, but I've tried so may settings but cannot get evolution to connect. Anyone also having had this problem and finally solved it? I also tried DavMail with no luck. Any help appreciated!

---

### Post by wyliecoyoteuk on 2011-04-20
Evolution uses OWA to connect to exchange, so you need an http URL

---

### Post by mawe3661 on 2011-04-20
Sure, the OWA I have used is: [https://webmail.domain.com/exchange](https://webmail.domain.com/exchange) - I have also tried with http. On android you only need to specify webmail.domain.com. I have of course tried without exchange as well in evolution.

More ideas?

---

### Post by collisionystm on 2011-04-20
It does not work with Exchange 2007 or 2010. Atleast it never did for me. Evolution is crap. The performance isn't even worth the effort.

---

### Post by collisionystm on 2011-04-20
Now if only someone could port Androids Corporate Email Sync program to Ubuntu. That would be amazing. But alas, for now we have things like Zimbra ( my favorite ) thunderbird and the ugly red headed step child, evolution

---

### Post by dcstar on 2011-04-21
> **wyliecoyoteuk said:**
> Evolution uses OWA to connect to exchange, so you need an http URL

OWA only works on Exchange 2003, I have used Evolution on these with little problem.

You need to use the MAPI plugin for 2007/2010 and I believe that you need externally verified HTTPS certificates on the Exchange server.

People have posted that they can get Evolution to work on Exchange 2007/2010, but all these servers that I support have self-issued certificates and I have never been able to get it to work on these.

---

### Post by mawe3661 on 2011-04-26
Thanks for the posts. It is an Exchange 2003 server, so it should work. But I agree, why not port the android code which works like a charm. Or is it only bad evolution documentation/instructions that some people, including me, does not understand? Does it depend on how the server is set up?

---

