---
title: "Access Hardware firewall"
date: 2010-01-20
forum: General Help
---

### Post by pgp_protector on 2010-01-20
I'm running Ubuntu server 9.10 (Upgraded from 9.04 install)
I've also installed Webmin for administration.

Both of these work well.

These systems are at my house with a dynamic IP address (Semi fixed as it's DSL and I don't refresh the connection much)

What I want to do is access my networks Firewall / router.
It's configured to not allow external connections, only connections from inside the network.

But when I try to access it via the Webmin HTTP Tunnel I get 
"Error - Missing Content-Type Header"

Is their another form of proxy command I can do even via SSH so I can access my internal router through the Ubuntu box ?

I.E. My Computer at work -> My Ubuntu Computer at home -> My Router ??

---

### Post by kitserve on 2010-01-21
The way I do this sort of thing is via an ssh tunnel. If you run the command 'ssh -CD 9999 ' this will open the tunnel. You can the set Firefox to use the tunnel by going to Edit->Preferences->Advanced->Network->Settings. Select "Manual proxy settings" and make sure all proxies are blank apart from "SOCKS Host", which should be set to localhost on port 9999 with type SOCKS v5. Your Firefox browsing will now be tunneled through the server and you should be able to access the router.

---

### Post by pgp_protector on 2010-01-21
when I try ssh -CD 9999 I just get a usage: ssh prompt with how to use ssh.

if I try ssh -cd 9999 I get an error "Unknown cipher type 'd'"

---

### Post by kitserve on 2010-01-25
Those are capital letters, you need to enter -CD and not -cd.

---

