---
title: "Automate Multiple Hop/Layered SSH Tunneling?"
date: 2010-07-27
forum: General Help
---

### Post by krinderlin on 2010-07-27
At my work place, we use an SSH server attached to a VPN appliance to ssh into our client's servers for support purposes.  Often, we need to access http and https ports 8080 and 8443 on machines on their side of the VPN. 

This normally requires the following set of commands in 3 different terminals.  For simplicity's sake, I've also named the relevant servers.

[LIST]
[*]portal: our SSH server
[*]remote-portal: client's SSH server
[*]destination: the box whose ports I want to access
[/LIST]
[LIST=1]
[*]In the first terminal: 
```
# ssh portal-server
# ssh -gL 9999:remote-portal:22 user@remote-portal
```
[*]In the second terminal:
```
# ssh -L 9999:portal:9999 portal-server
```
[*] In the third terminal:
```
# ssh -L 9998:destination:22 user@remote-portal
```
[*] In the fourth terminal:
```
# ssh -L 8008:127.0.0.1:8080 -L 8443:127.0.0.1:8443 -p 9998 user@127.0.0.1
```
[/LIST]

Is there an easy way to automate building and tearing down this particular tunnel?  It's annoying to have to build this tunnel so often and I have to do it 2-3 times a day to about 3 different sites.  Because of the way the applications are written on the servers, I can't set up one site as 8080/8443 and the next as 8081/8444 and so on.

Distributing my public RSA key and forwarding through ssh-agent isn't a problem.

Thanks ahead of time for some advice on where to go with this.

---

