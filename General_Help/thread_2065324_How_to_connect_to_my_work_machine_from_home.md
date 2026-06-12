---
title: "How to connect to my work machine from home"
date: 2012-10-01
forum: General Help
---

### Post by niranjan_rao on 2012-10-01
I know about ssh, "-X" flag etc, but some how could not get the combination right and looking for the help.

My home laptop and work machine is ubuntu 12.04. Both are behind firewall. At work we have a ubuntu server that allows in coming connections to ssh from internet.

Normally if I want to connect to my work machine, I ssh into open server and then ssh again to my box. This works for terminal based programs.

I am wondering if there is a way to forward x thru the internmediate machine so that I can see GUI on my home machine. I have a feel this can be done using ssh port forwading and "-X" flag of ssh, but could not figure out how to do that. 

Tried VNC on windows machines feew years back. If I remember correctly, it "scrapes" the screen. So others can watch my screen and actions. Don't know if its true for ubuntu machines also.

Best solution might be to able to login to my desktop using remote desktop - again tunnelling thru ssh. In the worst case, I can requst admins to open firewall for required ports.

---

### Post by LewisTM on 2012-10-01
What happens if you try to ssh -X twice? I bet it works but it's very slow.

If possible I'd ask for the firewall to open a port for you, e.g. port 2345, and forward it to port 22 on your work machine. You would then connect with command
```
ssh -X -p 2345 user@work.domain
```
Id' also recommend adding the -C switch for compression unless your connection is very high speed.

Better yet, install [X2Go]("http://www.x2go.org/"), which features an ssh-based NX protocol for remote desktop sessions. It's much faster than ssh -X. 

Cheers!

---

