---
title: "installed apache on local, is it accesible by others?"
date: 2011-08-03
forum: General Help
---

### Post by loolooyyyy on 2011-08-03
everything has it's default password or doesnt have any, because i'm the only user, i'm not connected to any particular network, ***but directly connected to internet***
are my stuff(home folder,apache root folder: /var/www/, sqldatabases,...) in danger?

---

### Post by zero2xiii on 2011-08-06
hell yea,

Thats like saying "Hay I live on a farm, but I don't have a fence, gate or doors. Am I in danger of getting robbed?"

I suggest geeting atleast a firewall up and running, refusing all INBOUND connections... also, never ever use default passwords, and NEVER leave anything without passwords.

Directly connected to the internet is dangerous to begin with, leaving everything open is like putting up a "Welcome" sign.:confused:

:shock:

---

### Post by loolooyyyy on 2011-08-06
> **zero2xiii said:**
> hell yea,

Thats like saying "Hay I live on a farm, but I don't have a fence, gate or doors. Am I in danger of getting robbed?"

I suggest geeting atleast a firewall up and running, refusing all INBOUND connections... also, never ever use default passwords, and NEVER leave anything without passwords.

Directly connected to the internet is dangerous to begin with, leaving everything open is like putting up a "Welcome" sign.:confused:

:shock:

i have a wireless router, does that count? :D
how do i deny access of others to apache? just accessible by me

---

### Post by gizmo720 on 2011-08-06
If there is a router between your computer and the Internet, then you are safe. Any attacker would need to go through your router. Routers will handle all incoming requests themselves, unless you configure them to forward a specific port to your computer.

---

### Post by loolooyyyy on 2011-08-06
thanks, thousand times

---

