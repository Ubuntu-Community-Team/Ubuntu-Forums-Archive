---
title: "SSH tunnelling confusion"
date: 2011-02-25
forum: General Help
---

### Post by jon.mithe on 2011-02-25
Hi,

I'm struggling to understand something.  I have a development box on my LAN hosting various dev tools, i.e. [https://mybox/svn](https://mybox/svn).

I've enabled SSH on it and have poked a hole in my router firewall so I can access the box from the outside world.

Essentially I'm interested to access the tools hosted on the box from outside. However,for security reasons I'd rather not poke more holes in my router firewall and open up my hosted resources to the internet. 

I know its possible to setup a VPN connection I think, but I've heard its a pain to setup.

Just wandering if anyone knows if some sort of ssh tunneling would provide a solution to access to hosted resources on that box?

Thanks for any help, my knowledge of linux and this sort of networking is not particularly great :P

Jon

---

### Post by Sirion on 2011-02-25
Hi

there are two ways to access the services on your machine through ssh-tunnels:

1. If your client application supports a SOCKS-proxy, you can activate the socks proxy option in your ssh-client (should be "-D [port]") and then use "locahost:[port]" as proxy.

2. You can tunnel the specific (remote) port used by your application (for example 21 for ftp or 25 for smtp) to a (local) port (should be "-L [port]:localhost:[port]") and then access the service as if it was listening on your local machine "locahost:[port]"

Sometimes applications use more than that one port and it does not work that easily (for example active ftp vs. passive ftp).

HTH,
Jens

---

### Post by jon.mithe on 2011-02-25
Ah thats brilliant thanks, was playing with something similar but just could not get it to work until I saw your post (turns out I was always tunnelling the traffic to my router and not my development box)

So I used this command:

```
ssh <user>@<external-ip address> -L <local port>:<internal hostname>:<port> -N
```

So for https to ssh tunneling to my user on a box with hostname "mybox" using port 20000 on my external machine:

```
ssh jon@88.88.88.88 -L 20000:mybox:443 -N
```

and I can access it in the browser using [https://localhost:20000/svn](https://localhost:20000/svn) etc.  Or add a 127.0.0.0 mybox entry into /etc/hosts

Awesomes :)

Thanks again!
Jon

---

