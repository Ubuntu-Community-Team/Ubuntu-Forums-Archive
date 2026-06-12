---
title: "Is there a way to Tunnel a single application though a PPTP VPN?"
date: 2010-12-16
forum: General Help
---

### Post by lixoman100 on 2010-12-16
Hello,

I have a PPTP VPN configured in my system. What I want to do is write a script that automatically connects to that VPN, runs an application (some SVN commands) and then disconnects.

But it would be also very good if that PPTP connection applied ONLY to my SVN commands (or to the current terminal) because, otherwise, everytime my script runs and does all this, all the other connections in the system (this is going to run in a server) are likely to drop and connections made while the VPN is active are gonna drop when the script ends.

What is the best course of action in this case?

---

### Post by efflandt on 2010-12-16
I have never done PPTP because I never had anything I could PPTP to.  But I have done ipsec.  If PPTP interferes with other connections maybe it is a routing issue.  Do not put a default route on the PPTP connection, only routing specific to the computer or network you are connecting to.

Another alternative if you have an ssh server on the other end is ssh or related programs.  It is relatively easy to tunnel through ssh, and even though it uses encryption, if you use compression, it can often be faster than your network connection.  It can also be configured to use keys without any password or pass phrase, limited to specific commands, which can ease scripting.

---

### Post by lixoman100 on 2010-12-16
> **efflandt said:**
> (..) Another alternative if you have an ssh server on the other end is ssh or related programs.  It is relatively easy to tunnel through ssh, and even though it uses encryption, if you use compression, it can often be faster than your network connection.  It can also be configured to use keys without any password or pass phrase, limited to specific commands, which can ease scripting.

You're preaching to the choir, brother :)
Unfortunately I have to do all this to access the network of a client that uses Windows servers that I have to dance around. If it wasn't for that I wouldn't even be using SVN for this.

> **efflandt said:**
> (...) If PPTP interferes with other connections maybe it is a routing issue.  Do not put a default route on the PPTP connection, only routing specific to the computer or network you are connecting to. (...)

Yeah I haven't done PPTP on the command line (or any kind of VPN/tunneling, as a matter of fact), I have only been using the native PPTP support on the Ubuntu Desktop. I'll take a look to see if it is possible to create a custom route of some sort that uses the PPTP connection. Thank you for the idea.

---

