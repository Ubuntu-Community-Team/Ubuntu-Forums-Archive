---
title: "Running Ircd-hybrid"
date: 2009-12-09
forum: General Help
---

### Post by m4fia on 2009-12-09
I'm trying to run an Irc-hybrid server on my server. And i'm having a problem with it not being able to be seen outside of the local network. This wouldn't have been a problem if it wasn't for the point of we have tried it on a none test server, and on an Internet server.

Installing ircd-hyrid goes without a hitch, and even on the test server, when everything is forwarded correctly, it doesn't connect except for locally. Is there any specials config files that have to be edited for it to be able to be seen on  the internet?

Thanks.

---

### Post by Sin@Sin-Sacrifice on 2009-12-09
Did you set your router(s)?

---

### Post by m4fia on 2009-12-09
Yes, the first router is setup to forward to the 2nd router, 

All Broadband Devices(#1 Router) -> 192.168.1.4(#2 Router IP) -> 10.0.0.5(Server IP)

So there should be no reason for it not to work, not to mention that it is also DMZ'ed. As you can reach Port 80, and Port 843 (Flash Socket Server). Without a hitch.

---

### Post by LeonBlade on 2009-12-09
When SSH'd into the server and using the command:
```
telnet localhost 6667
```

It catches the IRC server fine.
However, if I try to telnet the server from outside the server itself:
```
telnet SERVER_IP_HERE 6667
```

It wont connect...
Is there something that should be done with the **ircd.conf** file?  

I've installed ircd before on another server and didn't have this problem, so I have no idea what is wrong.

Thanks.

---

### Post by m4fia on 2009-12-09
Also doing a telnet locally doesn't accept connections. Though doing a telnet to any other service does get a response. So it shouldn't be anything with a router. I changed the 
```

vhost = "192.168.1.1"

```

to

```

vhost = "10.0.0.5"

```

Is this correct or should I change it to the Internet IP?

---

### Post by Chesamo on 2009-12-09
I had a problem with this... you have to edit the AUTH for the nomral users class in ircd.conf. It looks like this on my server:
```
auth {
	user = "*@*";
	class = "users";
	have_ident = no;
};
```
Also, I just commented out the vhost. (# sign in front of the line).

---

