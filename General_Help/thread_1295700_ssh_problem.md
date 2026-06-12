---
title: "ssh problem"
date: 2009-10-19
forum: General Help
---

### Post by zomglings on 2009-10-19
I'm running Ubuntu 9.04 and have been trying to set up an ssh server on my machine for the last couple of days. I have no trouble with *ssh localhost*, but whenever I try accessing my machine remotely, the connection keeps timing out.

I originally thought it was a firewall problem so I disabled ufw and flushed iptables and tried again. Nothing.

Then I thought maybe my university was blocking port 22 or something, so I tried on other ports with no success. I called them and they said that they were not restricting any access, anyway.

I thought it might be a problem with ipv6 so I disabled it in sshd_config (*AddressFamily inet)*. No success.

When I'm trying to establish a connection remotely and I run netstat on my local machine, it tells me that the connection has been established, but I am not being prompted for a password on the remote machine. Here is the output of ssh -vv:
ssh -vv $domain
OpenSSH_3.9p1, OpenSSL 0.9.7a Feb 19 2003
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to $domain ($ipaddress) port 22.
debug1: connect to address $ipaddress port 22: Connection timed out
ssh: connect to host $domain port 22: Connection timed out

I'm completely at a loss here, any help would be greatly appreciated!

---

### Post by P4man on 2009-10-20
are you trying to connect through a (university) router with NAT addressing? Even if they dont block anything, if you have a non public IP address on the server, youre not gonna be able to connect without port forwarding (or setting up a reverse ssh tunnel).

Can you try connecting from a different machine on the same network ?

---

### Post by Primefalcon on 2009-10-20
if your connecting from any outside connection for ssh you need port forwarding, which means you need access to the router

---

### Post by Lars Noodén on 2009-10-20
You can log in from *localhost*.  That's a good sign.  Can you log in from another machine on your LAN?  

Then, if so, try probing from outside your LAN, where *xx.yy.zz.aa* is your externally visible IP number:  

```
sudo scanssh -n 22 -s ssh *xx.yy.zz.aa*
```

---

### Post by Sethleben on 2009-10-20
I have exactly the same issue. According to my sysadmin, SSH via port 22 to machines on the network is allowed from external IP addresses. I have sshd running happily on my machine, and can SSH to localhost without problem. However, connections from external IPs time out. Disabling the firewall makes no difference. Using Wireshark to capture SSH packets, I see that the packets are actually reaching my machine, but for some reason I am not offered a login prompt unless the connection originates from localhost.

---

### Post by PatrickBoyle on 2009-10-20
Primefalcon is on the right track. The network device that is doing your university's NAT needs to know to forward traffic from the outside on port 22 to your machine's internal IP address.

Convincing them to do that is another story. Good luck.

---

### Post by Baelus on 2009-10-20
Is the ssh server computer inside or outside the university network?

---

### Post by zomglings on 2009-10-20
The ssh server is inside the university network. I'm trying to connect from my office, where the computer is also inside the university network.

Running scanssh kept timing out even from my machine. Don't know what the deal is with that.

I tried running nmap from a computer outside the network today, and it couldn't connect with my computer.

I'll try to find the right person to talk to in the IT office to forward the port 22 traffic.

Thanks for the suggestions! :)

---

### Post by DGortze380 on 2009-10-21
> **zomglings said:**
> The ssh server is inside the university network. I'm trying to connect from my office, where the computer is also inside the university network.

Running scanssh kept timing out even from my machine. Don't know what the deal is with that.

I tried running nmap from a computer outside the network today, and it couldn't connect with my computer.

I'll try to find the right person to talk to in the IT office to forward the port 22 traffic.

Thanks for the suggestions! :)

Just because they're both inside the University doesn't mean they're on the same network segment. Or the same network for that matter.

Good luck, I would say this is probably a lost cause. Getting IT to forward the correct ports at all necessary locations is going to be a long shot at best. There may be various levels of PAT going on here, not to mention firewalls, proxies, etc... The route between those two machines may be more complex than you realise.

---

### Post by zomglings on 2009-10-22
> **DGortze380 said:**
> Just because they're both inside the University doesn't mean they're on the same network segment. Or the same network for that matter.

Good luck, I would say this is probably a lost cause. Getting IT to forward the correct ports at all necessary locations is going to be a long shot at best. There may be various levels of PAT going on here, not to mention firewalls, proxies, etc... The route between those two machines may be more complex than you realise.

Good point. There are actually labs in my apartment building which I believe are on the same network (well, not knowing anything, I say so because the IP addresses differ only in the last three digits). Even from there it's impossible to connect.

But yeah, after talking to them today it looks like it's going to be hard to even get a line of communication open with the right people.

---

### Post by P4man on 2009-10-22
Hamachi should let you allow to remote access your machine despite firewalls and nat routers. I havent tried it myself yet, but have a look here:

[http://en.wikipedia.org/wiki/Hamachi](http://en.wikipedia.org/wiki/Hamachi)

---

### Post by Lars Noodén on 2009-10-22
> **zomglings said:**
> 
Running scanssh kept timing out even from my machine. Don't know what the deal is with that.


It means that SSH is not available at all and so you have to look at and solve other connectivity issues first.  The machine that has sshd running, you said you can connect using 'ssh localhost'.  It must have some external IP number, can you ssh using the external IP number on that same machine?

> **zomglings said:**
> There are actually labs in my apartment building which I believe are on the same network (well, not knowing anything, I say so because the IP addresses differ only in the last three digits). Even from there it's impossible to connect.

Try a traceroute from one machine to the other machine using the ip number.

[INDENT][FONT="Courier New"]traceroute -n *xx.yy.zz.aa*
# or try the same using TCP SYN to port 80 of the remote host
sudo traceroute -T -p 80 in *xx.yy.zz.aa*[/FONT][/INDENT]

If that does not work, try traceroute from both locations out to a common, public address such as google to see what networks are in the way.

---

### Post by DGortze380 on 2009-10-22
> **P4man said:**
> Hamachi should let you allow to remote access your machine despite firewalls and nat routers. I havent tried it myself yet, but have a look here:

[http://en.wikipedia.org/wiki/Hamachi](http://en.wikipedia.org/wiki/Hamachi)

Not quite ... if he can't ssh, ping or traceroute to the box, he won't be able to VPN to it either. I think you're misunderstanding the wiki.

---

### Post by P4man on 2009-10-22
> **DGortze380 said:**
> Not quite ... if he can't ssh, ping or traceroute to the box, he won't be able to VPN to it either. I think you're misunderstanding the wiki.

Thats entirely possibly. But it does state 

> When establishing tunnels between the peers, Hamachi uses a server-assisted NAT traversal technique, similar to UDP hole punching. Detailed information on how it works has not been made public. The vendor claims "...to successfully mediate P2P connections in roughly 95% of all cases ..

Sounds to me like me like this is similar to crossloops approach, where client software on the "server" establishes a (reverse) tunnel to a webservice, to which the client also connects  so you dont need port forwarding on your NAT router. The incoming traffic is tunneled through a.. hmm tunnel initiated by the server (hence no need for incoming ports). Should work on almost all firewalls and routers.

---

### Post by DGortze380 on 2009-10-22
> **P4man said:**
> Thats entirely possibly. But it does state 



Sounds to me like me like this is similar to crossloops approach, where client software on the "server" establishes a (reverse) tunnel to a webservice, to which the client also connects  so you dont need port forwarding on your NAT router. The incoming traffic is tunneled through a.. hmm tunnel initiated by the server (hence no need for incoming ports). Should work on almost all firewalls and routers.

Only if there's a route ...

If (due to firewall limitations, or network design) there is simple no route between the two machines, nothing is going to work.

---

### Post by P4man on 2009-10-22
> **DGortze380 said:**
> Only if there's a route ...

If (due to firewall limitations, or network design) there is simple no route between the two machines, nothing is going to work.

dont know if it can be routed through hamachi. In theory if both machines can connect to hamachi, then its possible, if they provide that service. Since they mention p2p, I guess not. Anyway its still worth trying  and more likely to work than asking IT to forward a port ;)

---

### Post by DGortze380 on 2009-10-22
> **P4man said:**
> and more likely to work than asking IT to forward a port ;)

Agreed, ANYTHING is more likely than IT forwarding stuff all of campus for him.

---

### Post by karlson on 2009-10-22
> **Sethleben said:**
> I have exactly the same issue. According to my sysadmin, SSH via port 22 to machines on the network is allowed from external IP addresses. I have sshd running happily on my machine, and can SSH to localhost without problem. However, connections from external IPs time out. Disabling the firewall makes no difference. Using Wireshark to capture SSH packets, I see that the packets are actually reaching my machine, but for some reason I am not offered a login prompt unless the connection originates from localhost.

You may want to set:

UseDNS=no

Also.

Check that you don't have ListenAddress not set.

Once done run sshd in debug mode:

```

sudo /etc/init.d/ssh stop
sudo "/usr/sbin/sshd -ddd >& /var/tmp/sshd.debug.log"
sudo /etc/init.d/ssh start

```

Once sshd comes up in debug mode try connecting again.  If sshd sees the packets coming in then it will tell you why the connection is refused.

---

### Post by zivley on 2009-10-22
What is your default gateway?
Open a terminal and do
```
netstat -rn
```
and post the results
ALso, please try to disable apparmor and try to connect to the machine again
```
sudo /etc/init.d/apparmor stop
```

---

### Post by zomglings on 2009-10-23
> **Lars Noodén said:**
> It means that SSH is not available at all and so you have to look at and solve other connectivity issues first.  The machine that has sshd running, you said you can connect using 'ssh localhost'.  It must have some external IP number, can you ssh using the external IP number on that same machine?



Try a traceroute from one machine to the other machine using the ip number.
[INDENT][FONT=Courier New]traceroute -n *xx.yy.zz.aa*
# or try the same using TCP SYN to port 80 of the remote host
sudo traceroute -T -p 80 in *xx.yy.zz.aa*[/FONT][/INDENT]If that does not work, try traceroute from both locations out to a common, public address such as google to see what networks are in the way.

Yeah, really sorry about that, that's something I should have mentioned before. I can ssh from my machine to itself using the ip address rather than with ssh localhost. It works perfectly well.

Got my new laptop today, so I don't have to keep shuffling up and down anymore. traceroute from the laptop works in one step (I mean the computers are at distance 2 from each other).

> **zivley said:**
> What is your default gateway?
Open a terminal and do
```
netstat -rn
```and post the results
ALso, please try to disable apparmor and try to connect to the machine again
```
sudo /etc/init.d/apparmor stop
```

Sure, turning off apparmor did nothing. Here's the routing table:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
149.159.16.0    0.0.0.0         255.255.254.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         149.159.16.1    0.0.0.0         UG        0 0          0 eth0

```
Out of curiosity, what does the destination column mean? My limited understanding (due to wikipedia) is that if I want to communicate with an ip address not in the network immediately accessible to me, it will forward the request to 149.159.16.1 and that computer will talk to its boss and so on. Is that right? Don't know what the destination column is all about.

It's kind of cool how everything works.

---

### Post by zivley on 2009-10-23
You've got it SO right, as a person with "limited understanding" as you claim you couldn't get it better and explained in such a simple way.
The "0.0.0.0" destination is whatever isn't mentioned in the other subnets ranges, it means "any"
Routing works always from most speciffic to less speciffic, so the "last resort" is your default gateway, in your case is 149.159.16.1

---

### Post by yeats on 2009-10-23
Does the campus facility where your server is hosted host other servers for non-IT folks?  Meaning, that if they do, this is almost certainly a problem they've had to encounter before.  If yours is a "special case" somehow, though, you might ask your IT department if they are willing to give your box its own public IP.  If not that, they might consider setting up a VPN or giving you access to a box you can tunnel through...

---

