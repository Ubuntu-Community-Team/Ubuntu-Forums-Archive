---
title: "Login Server"
date: 2010-11-26
forum: General Help
---

### Post by cpressland on 2010-11-26
Hey Guys wassup?

We're about to deploy Ubuntu on 150+ PCs at work and we need a 'Login Server' kinda like Active Directory.

What we'd like is a server side way of creating users like:

[LIST]
[*]admin
[*]ThreeCold
[*]ThreeWarm
[*]SSETalk
[/LIST]

Then join the Ubuntu PCs to the login server so we don't have to manually create the users on every machine, we'd also like to be able to customise something on one machine, have it saved to the server, then lock that profile so that if a user 'breaks' something all they have to do is logout and back in to recreate the user profile on the local machine.

Any help / ideas would be great.

Thanks

Chris

---

### Post by HermanAB on 2010-11-26
Howdy,

You need NIS+

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=NIS%2B+howto](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=NIS%2B+howto)

---

### Post by cpressland on 2010-11-26
Thats CRAZY complicated, seriously, if this is the best Linux / Ubuntu has right now then it really has got a long way to go. Both Apple Name Server and Microsoft Active Directory are incredibly easy to setup, I don't understand why this has to be so complicated. It's a very simple concept.

Any other ideas?

---

### Post by Old_Grey_Wolf on 2010-11-26
Google LDAP. Here is one link describing what I think you are looking for [http://ldots.org/ldap/](http://ldots.org/ldap/).

---

