---
title: "Connecting to OpenLDAP on localhost using ldaps:///"
date: 2011-02-21
forum: General Help
---

### Post by Caudovittatus on 2011-02-21
Hi,
 
I wonder if anyone is able to help with this. I've just setup OpenLDAP on Ubuntu Server 10.04.2 following this guide:
 
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
 
It's mostly working well, but I do have one issue. I thought that after configuring TLS that it would be best to disable access via other means to keep connections to the LDAP server more secure, before doing so I wanted to check that I could actually connect to OpenLDAP on the localhost using the following command:
 
ldapmodify -Y EXTERNAL -H [ldaps:///](ldaps:///)
 
But got the following output:
 
TLS: can't connect: (unknown error code).
ldap_sasl_interactive_bind_s: Can't contact LDAP server (-1)
additional info: (unknown error code)
 
This looks like some simple misconfiguration on my part, but I can't see where it's wrong, nor could I find any answers by googling.
 
I should point out that I'm able to connect to the LDAP server from a different host on the network using [ldaps:///](ldaps:///) (via Apache Directory Studio), so I'm quite surprised that I can connect from another system, but not via the loopback.
 
At this stage this is really a learning exercise for me, I just want to get to grips with LDAP and I find that when starting out the best thing to do is play with the actual configs to get to know my way around, but this has me stumped.
 
I imagine this is either a very simple config issue or I'm trying to do something that isn't necessary. I'd really like to understand what I'm doing wrong or alternatively why trying to do this is unnecessary/irrelevant.

[Edit] In summary my main goal is to only allow secured access to the LDAP server, not transmit data in plaintext across the network.
 
Many thanks in advance for your time.

---

### Post by Caudovittatus on 2011-02-22
Some more hunting/experimentation revealed the solution to my not being able to connect to localhost via ldaps (port 636) or TLS (port 389).

As I suspected it was a simple config issue; the LDAP client needed to know where the CA certificate was located.  To do this, I needed to edit:

/etc/ldap/ldap.conf

And add the line:

TLS_CACERT /etc/ssl/certs/cacert.pem

Now I can make connections via ldaps/TLS reliably both externally and on localhost.

As a side note, I happened across another thread where someone had the same issue (and it seems there was a bug in that case, which is obviously now fixed).  That thread was at:
[http://ubuntuforums.org/showthread.php?t=1538527](http://ubuntuforums.org/showthread.php?t=1538527)

---

