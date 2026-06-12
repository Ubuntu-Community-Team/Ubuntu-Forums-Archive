---
title: "Why is port 53/tcp open?"
date: 2012-04-27
forum: General Help
---

### Post by caffeinated blood on 2012-04-27
After installing Ubuntu 12.04 yesterday and running an nmap scan I found that port 53/tcp is open: domain service. This was during a scan of the localhost. Another scan of my IP address is showing the same port and others open, but I am certain this second scan is showing my IP provider's end. So, why is port 53 open and how can I close it?

---

### Post by haqking on 2012-04-27
> **caffeinated blood said:**
> After installing Ubuntu 12.04 yesterday and running an nmap scan I found that port 53/tcp is open: domain service. This was during a scan of the localhost. Another scan of my IP address is showing the same port and others open, but I am certain this second scan is showing my IP provider's end. So, why is port 53 open and how can I close it?
 
it is for DNS you want it open if you want DNS to work ;-)
 
See this link [Dangertux guide to firewall]("http://ubuntuforums.org/showthread.php?t=1876124")

---

### Post by caffeinated blood on 2012-04-28
Well that's great if port 53 is 'supposed' to be open. However, if this port needs to be open for internet use - Why has it never appeared in nmap scans on previous Ubuntu versions with fully functional internet access?

---

### Post by poonjabi on 2012-04-28
> **caffeinated blood said:**
> Well that's great if port 53 is 'supposed' to be open. However, if this port needs to be open for internet use - Why has it never appeared in nmap scans on previous Ubuntu versions with fully functional internet access?

I've been wondering this myself too.

---

### Post by SeijiSensei on 2012-04-28
TCP port 53 is used for domain transfers; the only reason I can see it being open is if the OP is running a DNS server.  DNS servers also listen on UDP port 53 to accept queries from client resolvers.

Port 53 was open on my 12.04 machine because I had an instance of bind9 running, and it was listening to that port.  I probably installed it for testing purposes at some point or another.  I stopped it (with 'sudo service bind9 stop') and confirmed I can still resolve names as I expected.  

OP:
Run the command "sudo netstat -plnt" to see a list of which programs are listening on which TCP ports.  (Replace "t" with "u" in the options to view TCP ports or use -plntu to see both.)  What program is bound to port 53?

---

### Post by poonjabi on 2012-04-28
> **SeijiSensei said:**
> TCP port 53 is used for domain transfers; the only reason I can see it being open is if the OP is running a DNS server.  DNS servers also listen on UDP port 53 to accept queries from client resolvers.

Port 53 was open on my 12.04 machine because I had an instance of bind9 running, and it was listening to that port.  I probably installed it for testing purposes at some point or another.  I stopped it (with 'sudo service bind9 stop') and confirmed I can still resolve names as I expected.  

OP:
Run the command "sudo netstat -plnt" to see a list of which programs are listening on which TCP ports.  (Replace "t" with "u" in the options to view TCP ports or use -plntu to see both.)  What program is bound to port 53?

I have a fresh install of 12.04. 

Does this look normal:

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      938/smbd        
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1803/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1077/cupsd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      938/smbd        
tcp6       0      0 :::139                  :::*                    LISTEN      938/smbd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      1077/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      938/smbd        

```

Do you have any recommendations for me to block anything?

---

### Post by SeijiSensei on 2012-04-28
```
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1803/dnsmasq
```

OK, that's what I thought might be happening.

12.04 now runs dnsmasq, a compact DNS server.  The reasoning for this, [according to the developers]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/"), is to handle situations where your machine has multiple network interfaces with different DNS servers.  This can pose problems for people using virtual private networks (VPNs) and in other so-called "multi-homed" contexts.  (Personally, I think this approach is overkill since the proportion of users facing this problem is pretty small.)

**So starting with 12.04 every Ubuntu machine will be running a local DNS server by default.  However** it should only be listening to port 53 on the localhost (127.0.0.1) interface as shown in the netstat results you posted.  **This doesn't pose a security threat since the localhost interface isn't visible from outside your machine.**  If you scan your machine from another machine on the network with a tool like nmap, you should not see an open port 53.

So, no, this isn't a security problem, but I'm sure it's going to confuse some people for a while.  

(The decision to use resolvconf to rewrite /etc/resolv.conf, which is also discussed in Graber's post, has some significant "[fallout]("http://ubuntuforums.org/showthread.php?t=1914807")" as well, but not relevant to the issue here.)

These are fairly major changes in the way Ubuntu handles name resolution, ones that make 12.04 different from all previous releases and from other Linux distributions.  I've specifically disabled all of this stuff on my machine because I use my own custom resolv.conf file and my own local nameservers to resolve names.  For people like me these changes created problems where none existed before.

The claim in Dangertux's firewalling howto that haqking linked to is definitely wrong. As caffeinated blood rightly observed, machines need not have either TCP or UDP port 53 open to resolve names successfully.

---

### Post by haqking on 2012-04-28
yeah sorry was confused here.
 
I was assuming it was seen as you were running a DNS service, as the only time a port is "open" is when a service is listening on it so i assumed you had DNS and therefore would require it.
 
I wasnt aware 12.04 had a DNS listening service running by default.
 
Peace

---

### Post by Dangertux on 2012-04-28
Umm yes you do need it open outbound but not inbound. Feel free to bang your head against a wall with that though...

---

### Post by iponeverything on 2012-04-28
> TCP port 53 is used for domain transfers; the only reason I can see it being open is if the OP is running a DNS server. DNS servers also listen on UDP port 53 to accept queries from client resolvers.

large results over UDP, exceeding 512 bytes, can cause the results to be truncated or for the query to fail all together. The first time I came across this was on one my firewalls many years ago - with cnn and google - So, TCP is used in these cases.

But there is no need to open 53/TCP INPUT - as it is covered by the normal "established/connected" behaviour of a masquerade for outgoing connections.

---

### Post by SeijiSensei on 2012-04-28
> **haqking said:**
> I wasnt aware 12.04 had a DNS listening service running by default.

I'm sure you're not alone, and you're an experienced user.  I'm guessing this won't be the last time this question gets asked now that 12.04 is released.

> **Dangertux said:**
> Umm yes you do need it open outbound but not inbound. Feel free to bang your head against a wall with that though...

Unless my default OUTPUT policy is DROP, I don't see why I'd need to injure myself like that.  On routers for networks where I can't trust the hosts behind them, I might set the OUTPUT policy to DROP, but on individual client machines, especially ones behind firewalls, it seems like overkill.  I'm not really worried about malware on machines I use, and even then I don't think I could protect against some miscreant pieces of software.  I'd have to enable outbound connections to remote ports 80 and 443 for browsing, so any malware that makes HTTP or HTTPS connections to remote servers would be permitted anyway.

Outbound port 25 requests from spambots are a common problem on Windows networks, and I do block those at the router even with a generally permissive OUTPUT policy.  I also block all connections from local high ports to remote high ports on network routers for organizations that don't want their users to run torrents or use streaming video or audio services. We also proxy all HTTP requests through Squid and block a lot of bad behavior with ACLs.

> **iponeverything said:**
> large results over UDP, exceeding 512 bytes, can cause the results to be truncated or for the query to fail all together.

I saw evidence for this just the other day at a client site where named was logging EDNS errors.  I think there's an ancient Cisco router between them and the Internet that might be responsible for the problem.  I disabled logging for that error, but I think the better solution is to [disable EDNS queries entirely]("http://www.linuxquestions.org/questions/linux-newbie-8/dns-issues-bind-9-7-3-a-933485/").

---

### Post by Dangertux on 2012-04-28
Yeah I'm just pointing out that the guide of mine that was linked is using a default outbound drop policy... so if you're following that you need to allow access to an external DNS server lol :-P

---

### Post by haqking on 2012-04-28
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

5th Bullet Point.

Its built into Network manager now.

so

```
/etc/NetworkManager/NetworkManager.conf
``` 

and comment the ```
dns=dnsmasq
```

line then do a 

```
sudo restart network-manager
```

Peace

---

### Post by caffeinated blood on 2012-04-29
Thank you 'haqking'! That closed the port/service. I'll mark this thread as solved.

---

### Post by tim71 on 2012-05-18
Currently it looks like NetworkManager kind of ignores this line in configuration

```
dns=dnsmasq
```

as the port is always open when dnsmasq is running and nslookup always indicate 127.0.0.1#53 as a server.

Only way to affect this seems to run or not to run dnsmasq.

Also weirdly enough it looks like dnsmasq is listening on all interfaces

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1350/mysqld          
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      8319/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1149/cupsd          
tcp6       0      0 :::53                   :::*                    LISTEN      8319/dnsmasq    
tcp6       0      0 ::1:631                 :::*                    LISTEN      1149/cupsd  
```

Which is interesting because dnsmasq had not been installed on this machine previously i.e. does not have other configuration beside default one - /etc/dnsmasq.conf is untouched (all options commented out) and /etc/dnsmasq.d/ is empty.

I don't know if there is any difference because system is upgraded and not fresh install, but this case here still implies, that this thing does not work 100% like advertised...

---

