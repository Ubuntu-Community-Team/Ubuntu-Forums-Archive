---
title: "freenx dyndns public key issue"
date: 2006-06-15
forum: General Help
---

### Post by dananimal on 2006-06-15
I'm having a weird problem with free nx on ubuntu 5.10

I have installed freenx and can use it fine from my LAN.
(Using the nomachine client on OS X 10.4.6)

I have installed and configured ipcheck to operate with dyndns and have configured the routers so that i can access my ubuntu box with ssh from outside of my LAN.

No problem so far.

Now.

When I try to access the same machine with freenx using the dyndns name it fails.
```
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```

i can connect with the command 
```
ssh -i /usr/NX/share/keys/server.id_dsa.key nx@192.168.0.4
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 
quit
Quit
NX> 999 Bye
Connection to 192.168.0.4 closed.

```
but return this when accessing via the dyndns name
```
ssh -i /usr/NX/share/keys/server.id_dsa.key nx@dyndns.ath.cx
nx@dyndns.ath.cx's password: 

```

This indicates to me that there is something amiss with the public key, that it isn't applying to the dyndns name as it is for the ip address.

I'd love some assistance on this as it is doing my head in ](*,)
(and yes I plan to upgrade to dapper as soon as I have a copy)

---

### Post by dananimal on 2006-06-16
I (kinda) successfully connected to my machine from outside today...
Success with the connection then nx times out before the x-session gets fully resolved.

alas try try again.

wish me luck

---

