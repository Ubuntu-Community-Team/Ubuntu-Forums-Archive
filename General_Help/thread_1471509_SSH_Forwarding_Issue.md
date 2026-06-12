---
title: "SSH Forwarding Issue"
date: 2010-05-03
forum: General Help
---

### Post by MK_MIke on 2010-05-03
Hey,

I'm trying to mirror a web server i have in an external location,  and i want to be able to set the private computer on my network which is mirroring the server to be available through the public server on the internet through port 8888. i can do this, but the port is only available through localhost on the server and  not publicly. basically I'm trying to port forward an apache server, so if need be i can access it through the web server.

I have tried opening up the port through the firewall etc with still no luck, I was wondering if there's some kind of built in restriction in SSH that prevents this happen for security reasons.

Thanks :D

---

### Post by Brandon Williams on 2010-05-04
From the man page for ssh:

    > -g      Allows remote hosts to connect to local forwarded ports.

I'm not sure that's required, though. What does your -L argument look like? As long as it doesn't specify "localhost" as the bind address, it should be fine. Try with -g, though, just to be sure that's not it.

---

### Post by v1ad on 2010-05-04
make sure you forward your ports on the router also.

---

### Post by MK_MIke on 2010-05-04
> **Brandon Williams said:**
> From the man page for ssh:

    

I'm not sure that's required, though. What does your -L argument look like? As long as it doesn't specify "localhost" as the bind address, it should be fine. Try with -g, though, just to be sure that's not it.

Hey,
 
I tried "ssh -g -R 1234:localhost:23 [email]mknights@****.co.uk[/email] -p 6969" with no luck.. when I am connected i can use lynx to connect to the port, which brings up the html page from my private system, but i still cant access this from a public computer.

tcp6       0      0 ::1:1234                *:*                     LISTEN     32670/0


So the port is there listening...

Also there is not external firewall to prevent connections.

Thanks for your help,

Mike

---

### Post by MK_MIke on 2010-05-05
(bump)

---

### Post by efflandt on 2010-05-05
Re: -R

By default, the listening socket on the server will be bound to the loopback interface only. This may be overridden by specifying a bind_address.  An empty bind_address, or the address ‘*’, indicates that the remote socket should listen on all interfaces.  Specifying a remote bind_address will only succeed if the server's **GatewayPorts** option is enabled (see sshd_config(5)).

Is there any mention of **GatewayPorts** in the sshd_config of the sshd server?

---

### Post by MK_MIke on 2010-05-05
> **efflandt said:**
> Re: -R

By default, the listening socket on the server will be bound to the loopback interface only. This may be overridden by specifying a bind_address.  An empty bind_address, or the address ‘*’, indicates that the remote socket should listen on all interfaces.  Specifying a remote bind_address will only succeed if the server's **GatewayPorts** option is enabled (see sshd_config(5)).

Is there any mention of **GatewayPorts** in the sshd_config of the sshd server?

GatewayPorts wasn't in the config at all but after adding it, everything started working.

Thanks this solved my problem,

Also thanks to everyone who helped me with this issue.

Mike

---

