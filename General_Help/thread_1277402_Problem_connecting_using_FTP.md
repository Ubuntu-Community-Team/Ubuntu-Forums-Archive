---
title: "Problem connecting using FTP"
date: 2009-09-28
forum: General Help
---

### Post by fantastic on 2009-09-28
I have been having difficulties trying to connect to an FTP server. I'm running Ubuntu 9.04.

When I use passive mode to connect, it establishes the connection immediately but cannot read the FTP server's directory and just hangs. When I try to connect in standard more (not using passive mode), I get the following message in FireFTP:

```
500 I won't open a connection to 127.0.1.1 (only to XXX.XXX.XXX.XXX)
: //
```

I have completely disabled the Ubuntu iptables firewall and now allow all INPUT, OUTPUT and FORWARD connections:


```
Chain INPUT (policy DROP 3035 packets, 1485K bytes)
 pkts bytes target     prot opt in     out     source               destination         
52654   29M LOG        all  --  any    any     anywhere             anywhere            LOG level warning 
52654   29M ACCEPT     all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level warning 
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            

Chain OUTPUT (policy ACCEPT 248 packets, 17728 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 4866  729K ACCEPT     all  --  any    any     anywhere             anywhere 
```

I've tried using various FTP clients- e.g. shell, FireFTP and Filezilla.

I tried connecting from a Fedora box and had the same issue. When I connect from a Windows box, I am able to connect.

The FTP server I'm connecting to is a black box FTP server running on a non-standard port. I do not have the ability to see the FTP logs. I can only enter IP address permitted to access it; and yes I've triple checked to make sure the correct IPs have been entered correctly on the server to allow those machines to have access to it.

Any help appreciated. Thanks.

---

### Post by Giblet5 on 2009-09-28
Are you trying to connect through some other firewall (corporate router, DSL Router From Hades, etc)?

You may need to use socksify.

---

### Post by fantastic on 2009-09-28
I always do this... (which is why I usually preview my post, let it set for another 10 minutes and then finally post it because I somehow think of what I did wrong by writing a post).

The problem is resolved.

I started thinking about that 127.0.1.1 and how it didn't make sense. 

My /etc/hosts was:
```
127.0.0.1 localhost
127.0.1.1  myComputerName
```


I changed the 127.0.1.1 to my actual static IP address of my computer. So it looks like this:
```
127.0.0.1 localhost
XXX.XXX.XXX.XXX  myComputerName
```


I then ran:
```
sudo /etc/init.d/hostname.sh
```


Problem resolved.

Hopefully this helps someone else in the future.

---

### Post by mhdbnoimi on 2011-06-04
> **fantastic said:**
> 
I changed the 127.0.1.1 to my actual static IP address of my computer. So it looks like this:
```
127.0.0.1 localhost
XXX.XXX.XXX.XXX  myComputerName
```

Does any one konws another solution because this solution makes make my PC crazy with other websites!

---

### Post by jamesisin on 2011-06-04
I question the wisdom of making that particular change.  All of my current systems include those two lines in their /etc/hosts file.  I recommend seeking out a better solution.

---

### Post by mhdbnoimi on 2011-06-04
> **jamesisin said:**
> I question the wisdom of making that particular change.  All of my current systems include those two lines in their /etc/hosts file.  I recommend seeking out a better solution.

Sorry I didn't get... what you mean?

---

### Post by jamesisin on 2011-06-04
That line in your /etc/hosts file is standard.  Something ELSE is causing your FTP problem.  Changing your /etc/hosts file will likely cause other problems (with anything that is relying on that particular address).

---

