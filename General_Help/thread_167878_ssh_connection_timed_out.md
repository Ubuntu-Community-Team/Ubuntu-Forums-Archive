---
title: "ssh connection timed out"
date: 2006-04-29
forum: General Help
---

### Post by the_tiger on 2006-04-29
I am trying to test my external ssh access. I can use ssh between machines internally and have used virtual server on my router to send port 22 as port 22 to another internal machines ip. I am now attempting to go out of and then back into my network using

ssh username@externalIP

however nothing happens and then I get connection time out.

HELP!

---

### Post by Slim Odds on 2006-04-29
Sounds like a routing problem. Can we get some kind of network diagram?

---

### Post by the_tiger on 2006-04-29
```

ssh client Machine 1------->
                           |--Modem Router <-------------> WAN External IP
                           |
ssh server Machine 2-------<

```

Port 22 is forwarded to machine 2.

---

### Post by Slim Odds on 2006-04-29
[quote=the_tiger]```

ssh client Machine 1------->
                           |--Modem Router <-------------> WAN External IP
                           |
ssh server Machine 2-------<

``` 
Port 22 is forwarded to machine 2.[/quote] 
There are a number of potential problems.

1) Can machine 1 get out to the outside network? What does it's routing table look like?
2) Is some other firewall or host blocking before it gets back?
3) Is ICMP working? try using traceroute to see how far you are getting
4) Is the WAN a private network? It may be dropping the traffic

---

### Post by the_tiger on 2006-04-29
I found the problem. Despite having forwarded the relevant ports I had intrusion detection turned on in my router firewall. This prevented me from sending a packet back out and in again as it looked like IP spoofing. Turned it off and it worked like a charm.

---

