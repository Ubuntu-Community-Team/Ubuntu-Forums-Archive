---
title: "Problem with ldap/ssl authentication"
date: 2010-11-15
forum: General Help
---

### Post by tommyold85 on 2010-11-15
Hello to everyone.
I've a question about ldap authentication.
[COLOR=#000000]This is the scenario[/COLOR]:i must configure linux and win client, [COLOR=#000000]so they can authenticate through an LDAP server[/COLOR]. T[COLOR=#000000]he server is configured to accept requests via SSL[/COLOR] so i should configure the clients to use it.
Everything works fine (both clients) if i connect to server on port 389. In the win systems i use pgina and it works fine without SSL but if i check SSL (on port 636 obviously) i'm unable to log in to the server. Using the ldp tools i retrieve the 0x51 error.
My questions are:
- Which certificates should I use?
- Can i use ssl without certificates?

---

