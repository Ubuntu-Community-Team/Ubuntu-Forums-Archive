---
title: "Anonymous SSH through proxy (TOR, PRIVOXY, PROXYCHAINS)"
date: 2006-04-08
forum: General Help
---

### Post by Prospero2006 on 2006-04-08
Hello all, 

I thought I'd throw this out there. I successfully connected to an ssh server a few minutes ago through a TOR proxy. It masked my ip address just the way I hoped it would. Here's how I did it. (Is there an easier way)

I installed TOR, Privoxy, and Proxychains.

In Proxychains.conf I made the proxy server 127.0.0.1:9050
(This request is then forwarded to the tor socks4 server) 

I type proxychains ssh (remotesshserver)

That successfully routes the ssh request through the tor network. 

Two questions then:
   -Can it be done more easily?
   -The tor network is slow as toenail fungus. (Like my simile?)
     Is there a way to specify which tor server you want to use 
     once you locate a fast one?

Thanks,
Pros

---

### Post by ubuntuuser on 2006-04-08
As far as I understand how TOR works, the traffic is routed through several, randomly selected servers, so I don't think you can specifically use only one router. Wouldn't make much sense anyway, because then you could just use an anonymous proxy instead. But if you want to help make TOR faster, consider running a server yourself. [Have a look here.]("http://tor.eff.org/docs/tor-doc-server.html")

---

### Post by j-strap2 on 2006-04-09
You can request your Tor circuits to use one or more specific Exit Nodes from the Tor network. The problem with this is that the Exit Nodes are heavily loaded and performance varies from time to time - you find a fast node and 10 minutes later, it runs like a dog. It is far better to allow Tor to choose you Exit Node, and better for your anonymity too.

---

