---
title: "Bind9 configuration for single word domain names"
date: 2012-10-08
forum: General Help
---

### Post by stefangr1 on 2012-10-08
I have been attempting to configure bind9 in such a way that I can ssh/browse to systems on the local network using single word domain names. E.g., typing synology1 in a webbrowser or ssh synology1 in a terminal should bring me to the right place.

However, with my current configuration (see below), it doesn't work. The first time, a dot needs to be added to the domain name (e.g. "synology1."). After that, simply typing "synology1" works correctly. This behavior is probably related to the fact that a single word without a dot is not a fully qualified domain name. However, I still wonder whether there's a solution to this, as - for example - many routers do seem to have this feature.

db.synology1 looks as follows:

```
@ IN SOA ns.server root.synology1 (
201003096 ; serial
8H ; refresh
4H ; retry
4W ; expire
1D ) ; minimum

@ IN NS ns.server
ns.server IN A 192.168.1.15
@ IN A 192.168.1.5
```

---

### Post by HereInOz on 2012-10-08
I know this is probably not the way you want to do it, but why not use the /etc/hosts file, and put the necessary entry in that.  

It will cause a problem if the IP address in the DNS records ever changes; I understand that, but it is a way around it.

---

### Post by stefangr1 on 2012-10-08
> **HereInOz said:**
> I know this is probably not the way you want to do it, but why not use the /etc/hosts file, and put the necessary entry in that.  

It will cause a problem if the IP address in the DNS records ever changes; I understand that, but it is a way around it.

Well, adding the "." at the end isn't that much of a problem, and it actually works well I suppoze. It just seems a bit silly that it is neccesary, and I don't understand why it somewtimes won't and sometimes will work without adding the final dot.

---

### Post by Doug S on 2012-10-09
The "dot" at the end is proper bind syntax for the db file. Your posted file is missing 3 "dots", and also missing a TTL declaration.
I have no comment about the trying to use single domain names part. You should be able to use one domain name and still be able to use one word only to specify which computer on your lan you desire. My internal lan, using bind, works that way. Example:```
doug@s16:~$ ping s15
PING s15.smythies.com (192.168.111.112) 56(84) bytes of data.
64 bytes from s15.smythies.com (192.168.111.112): icmp_req=1 ttl=64 time=0.296 ms
```

---

### Post by stefangr1 on 2012-10-10
> **Doug S said:**
> The "dot" at the end is proper bind syntax for the db file. Your posted file is missing 3 "dots", and also missing a TTL declaration.
I have no comment about the trying to use single domain names part. You should be able to use one domain name and still be able to use one word only to specify which computer on your lan you desire. My internal lan, using bind, works that way. Example:```
doug@s16:~$ ping s15
PING s15.smythies.com (192.168.111.112) 56(84) bytes of data.
64 bytes from s15.smythies.com (192.168.111.112): icmp_req=1 ttl=64 time=0.296 ms
```


I see. This seems a much better solution. Can you give a hint about how to get this working? I would be really grateful if you would be willing to post the bind9 configuration file that takes care of this.

---

### Post by Doug S on 2012-10-11
To have abbreviated computer names lookup properly on your LAN you need to do two things: Have bind working properly; Have your client and server computers know to add the domain name extention to the DNS request when using abbreviated names.
 
For the bind part refer to the Ubuntu 12.04 server guide [DNS chapter]("https://help.ubuntu.com/12.04/serverguide/dns.html"), [this thread ]("http://ubuntuforums.org/showthread.php?t=1884267&highlight=bind")and, perhaps, [this thread]("http://ubuntuforums.org/showthread.php?t=1849828&highlight=bind"). There are examples of bind db files in those threads.
 
For the client computers, when I typed:```
doug@s16:~$ ping s15
```The DNS request that was sent was this:```
2012-10-10 16:38:31.091201 IP 192.168.111.113.35437 > 192.168.111.1.53: 62927+ A? s15.smythies.com. (34)
```Where you can see that the "smythies.com" part was added by the computer "s16".
For clients that get their IP lease via DHCP, this should work.
For clients that use static IP addresses, they might need a dns-search directive added to the etc/network/interfaces file (I think. I don't have any static clients). Or, if you are using an older version of Ubuntu, where /etc/resolv.conf doesn't get overwritten, a search directive can be added there.
For my server itself, sometimes it works and sometimes not. I was trying to figure it out today, but now it is working. Currrently my resolv.conf file (which get created from other stuff) is:```
doug@doug-64:~/config/network$ cat /etc/resolv.conf
nameserver 127.0.0.1
nameserver 75.153.176.9
nameserver 75.153.176.1
nameserver 75.153.176.1
domain smythies.com
[COLOR=red]search smythies.com[/COLOR]

```Hope this helps, and let us know how it goes. I'll add to this thread if I remember something I forgot to mention. There is another good thread about this stuff that I have not found yet.

---

